# Effective Cycript - [Jay Freeman](http://twitter.com/saurik)

* Download [cycript zip](http://cycript.org)
* Modify running iOS / OS X apps
* Syntax is a hybrid of ObjC and Javascript
* REPL-like
* Grammar-level tab completion, but be careful, may execute code accidentally
* Bridges functions with @encode typecast
* Some weird differences with stack and heap due to the Javascript layer, can't really write full apps in Cycript
* The # prefix means description
* @ syntax behaves like ObjC
* You can use Javascript functions on arrays (e.g. slice)
* Console generates an autorelease pool for every command
## Cycript cocoapod
* pod repo add saurik git://git.saurik.com/podspecs.git
* Change in Build Settings C++ Standard Library Compiler Default, Other Linker Flags -stdlib=libstdc++ -Xarch_arm64 -stdlib=libc++
* Rename main.m to main.mm