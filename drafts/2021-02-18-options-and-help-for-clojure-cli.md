---
title: Command Line Options And Help Menus For Your Fast Clojure CLI
date: 2021-02-19
site/group: Recent
site/tags:
    - clojure
    - software
    - command-line app
---

I recently wrote about [how to build a fast command-line app with Clojure](/blog/building-a-fast-command-line-app-with-clojure/), but to be fair it's a bit of an exaggeration to call what I made an _app_. Where I left off was with a native, standalone executable, which is a great start for sure, but there's a long way to go until it's actually useful like something we would actually think of as an app.

The next step is to add command-line options and help menus, so people can have some clue about how to use it! The little utility I want to build is a tool to index the contents of a directory into a database. By "database" I mean a file, so my command line app will need to accept two arguments — an input directory and an output path for the resulting index.

This post picks up where my last post left off to add this functionality to the [skeleton command-line app](https://github.com/kiramclean/indexer/tree/74ffbbcb99f5a55048025c969d6a718cfc828506).

## Working with command line arguments

There are a few ways to handle adding command line arguments to an app like this. One is to just do it all by hand — inspect the `args` vector that gets passed into the `main` function and do stuff with it by parsing the values at each position. 

This is totally possible, but there's more stuff to handle than just taking `(first args)`, `(second args)`, and so on and passing those through the program. I want to handle optional arguments, and also have default arguments for when the optional ones are omitted by the user. I also want to validate the input, like making sure the arguments are the right type and format. I also might want to have sub-commands and handle arguments for _those_. Think CLI sub-commands like `brew info <package-name>` or `yarn add <package-name>`. 

All of this quickly ends up being a lot of boilerplate to write for a feature that is going to be very stable, so I think it makes sense to look for a library to handle it.

## Command line argument libraries

There are a couple of candidates. There's an [official Clojure tools.cli](https://github.com/clojure/tools.cli) library that's meant to handle exactly the kind of faffing with arguments I described above. There's also [cli-matic](https://github.com/l3nz/cli-matic), which uses the tools.cli library but adds another layer on top to provide an even more compact API. It appears to be pretty stable and has a very Clojurey README with a nice explanation of the differences and tradeoffs with the base `tools.cli` library, so I'm going to use this one.

Add `cli-matic/cli-matic {:mvn/version "0.4.3"}` to your `:deps` in `deps.edn` to use the library.

## App config for cli-matic

There are basically two steps to get `cli-matic` to handle command line arguments is write a config map for your app. The first is writing a configuration map for your app. The [README](https://github.com/l3nz/cli-matic/blob/master/README.md) has a great explanation and there are lots of [example projects](https://github.com/l3nz/cli-matic/tree/master/examples) you can copy to get started. This is what the config looks like for my app that takes two optional arguments:

```
(def CONFIGURATION
  {:app         {:command     "indexer"
                 :description "A utility to index the contents of your directory into a .ttl file"
                 :version     "0.0.0"}
   :global-opts [{:option  "input-dir"
                  :short   "in"
                  :as      "Input directory (source of files to index)"
                  :type    :string
                  :default #(.getAbsolutePath (io/file ""))}]
   :commands    [{:command     "build" :short "b"
                  :spec        ::GLOBAL-ADD-VALIDATION
                  :description ["Indexes the content of the given input-dir as RDF in a file at the given output-file"
                                ""
                                "The input-dir must exist and the output-file will be silently overwritten if it already exists."]
                  :opts        [{:option "input-dir" :short "in" :as "Input directory (source of files to index)"
                                 :type :int :default 0 :spec ::ODD-SMALL}
                                {:option "addendum-2" :short "b" :as "Second addendum (even)"
                                 :type :int :default 0 :spec ::EVEN-SMALL}]
                  :runs        add_numbers}
                 ]})
```

## Validating arguments

Adding validation to command line arguments is really simple with `cli-matic`. Like a good, modern Clojure library it uses [spec](https://clojure.org/guides/spec) behind the scenes to do the validation. Clojure spec is great for validating data, but it's not so great at communicating feedback. The error messages it returns are opaque and certainly wouldn't mean anything to a non-Clojure person.

For example I want to make sure that the input directory someone specifies to source the files to index exists and that the output file they give _doesn't_ already exist. I can easily add that the the config, but the error messages that produces are bad:

```
Global option error: Spec failure for global option 'input-dir'
-- Spec failed --------------------

  "/Users/kira/does/not/exist"

should satisfy

  exists?

-- Relevant specs -------

:indexer.core/input-dir-validation:
  babashka.fs/exists?

-------------------------
Detected 1 error
```

I can grok that, but I'm a Clojure developer. It's meaningless to most people.

This is where [expound](https://github.com/bhb/expound) comes in. Instead of writing specs like

```
(s/def ::input-dir fs/exists?)
(s/def ::output-name (complement fs/exists?))
```

We can use expound's 



















