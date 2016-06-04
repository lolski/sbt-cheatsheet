# SBT Cheatsheet

Are you a Scala first-timer who find yourself fighting with the build system for even the simplest of tasks? Then this guide is for you. If you are a Scala veteran that just never bothers to remember the syntax, then this is for you as well.

## Hello World

Prepare your project's base directory
```
mkdir -p hello-world             # your project dir
cd hello-world
touch build.sbt                  # sbt build definition file
mkdir -p src/main/scala          # .scala files goes here
touch src/main/scala/Main.scala  # your hello world program
```

`build.sbt` should contain
```
name         := "hello-world"     // you can change to any name
scalaVersion := "2.11.8"          // and pick any scala version you want
```

`Main.scala` might look like
```
object Main {
  def main(args: Array[String]): Unit = println("hello world!")
}
```

*(Optional) if you are using Git, this is how your .gitignore should look like*
```
./project/target
./target
```

Now run it from the base directory `hello-world`. You **must** run it from the base directory.
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