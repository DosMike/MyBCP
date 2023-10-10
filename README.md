# MyBCP

My Boostrapper for Cpp Projects is a set of scripts intended to ease the pain to 
get a CPP dev environ up and running and managing dependencies.

The main issue I have with CPP dev on Windows is, in one word: Libraries.

While you can get started pretty easily with CPP, using only the standard library and a 
compiler + IDE like MSVC /  Visual Studio, it is really annoying to find libraries, sometimes
they come without binaries, and then add include and lib path as well as the library name 
to the project for every build varaint and platform in Visual Studios is annoying.

Adding a build system like CMake to the mix eases this pain immensly, but this also requires
another tool to actually manage and make those available dependencies, because that's not the 
responsibility of the build tool.

I feel like this it is not controversial to say, that the tooling around C++ compared to
modern languages is really lacking on Windows. It is bearable on Linux because you can install
packages and build tools through the system package manager and everything is exposed through
dpkg and other built in utilities.

The situation on Windows is so bad, that the recommended way to use dependencies is to install
a linux environment to manage packages and tools, like MinGW, Cygwin, WSL, ... and suddenly
you are probably using GCC/CLang on Windows instead of MSVC because the build environment 
handles thoses better.

Languages like JavaScript, and Python show how easy it could be to get started with install
packages that include runtime, build tools and package manager at once, all developed from
an official place. Yes, the ecosystem around C++ has those features, but as a new dev I
don't want to install Python, because I want to install a package manager, to download the 
dependency, so I don't have to write another implementation of linked lists. It feels like
a lot of hoops to jump through, especially on Windows, and that has killed my insterest in
various projects for me.

But I guess I would not be a software developer if I didn't try to solve my problems with code!

This script will ease that set-up pain and create an opinionated template environment:
* Find a working compiler (MSVC 2019 and 2022 are supported)
* Get a package manager and build system up and running (Conan+CMake)
* Generate template build configs
* Build the damn thing and give access to a dev env shell

Since this is specifically intended to help with Windows, MSVC/VS will be used for compiling.
So we will search that, as in the most recent installed version.
The package manager is Conan, with CMake as build system. Conan has a wide variety of 
packages with the JFrog repository and the website tells you what to poke to get a dep into
CMake. It is simple enough for beginners while still offering flexibility for more complex
projects.

From there on, subsequent runs of the build script will search MSVC, load the dev env,
so Conan and CMake can find the compiler, make sure the dependencies are installed and
run you average CMake build.

## HowTo

Copy the build.bat and build._py files into your repository, run build
