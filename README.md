# SBT Cheatsheet

Are you a Scala first-timer who find yourself fighting with the build system for even the simplest of tasks? Then this guide is for you. If you are a Scala veteran that just never bothers to remember the syntax, then this is for you as well.

### Hello World

Let's go back to basic! This is how to prepare a project's base directory:
```
mkdir -p hello-world             # your project dir
cd hello-world
touch build.sbt                  # sbt build definition file
mkdir -p src/main/scala          # .scala files goes here
touch src/main/scala/Main.scala  # your hello world program
```

Contents of `build.sbt`:
```
name         := "hello-world"     // you can change to any name
scalaVersion := "2.11.8"          // and pick any scala version you want
```

`Main.scala` might look like:
```
object Main {
  // let's do a bare minimum, working example
  def main(args: Array[String]): Unit = println("hello world!")
}
```

If you are using Git, add the following directories to `.gitignore`. They are auto generated and you don't want them:
```
./project
./target
```

Now, try to run it from the base directory, `hello-world`. Remember, you **must** run it from the base directory.
```
sbt run
```

```
[info] Set current project to hello-world (in build file:/Users/lolski/Project/sbt-cheatsheet/01-initialization/)
[info] Updating {file:/Users/lolski/Project/sbt-cheatsheet/01-initialization/}root-01-initialization...
[info] Resolving jline#jline;2.12.1 ...
[info] Done updating.
[info] Compiling 1 Scala source to /Users/lolski/Project/sbt-cheatsheet/01-initialization/target/scala-2.11/classes...
[info] Running Main
hello world!
[success] Total time: 4 s, completed Jun 4, 2016 3:24:16 PM
```

Horray!


### Dependencies

Specify dependencies one by one in `build.sbt`:
```
name         := "hello-world"
scalaVersion := "2.11.8"
libraryDependencies += "org.apache.commons" % "commons-lang3" % "3.4"
libraryDependencies += "org.apache.commons" % "commons-io" % "1.3.2"
```

Alternatively, specify as a `Seq`
```
name         := "hello-world"
scalaVersion := "2.11.8"
libraryDependencies ++= {
  Seq(
    "org.apache.commons" % "commons-lang3" % "3.4",
    "org.apache.commons" % "commons-io" % "1.3.2"
  )
}
```

### Commands
These commands are
```
sbt run                                      # runs your program
sbt sbtVersion                               # displays sbt version
sbt console                                  # opens REPL console
sbt compile                                  # compiles project
sbt clean                                    # clean
sbt "test-only org.yourcompany.YourTestSpec" # runs a single test
sbt test                                     # runs every tests
sbt ";clean ;compile; run"                   # combines multiple commands in a single invocation
```
