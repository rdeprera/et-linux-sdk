# SDK para Wolfenstein Enemy Territory
Baseado no [SDK de Linux fornecido pela Splash Damage](https://www.splashdamage.com/games/wolfenstein-enemy-territory/) mas com atualizações:
- Alterado a sintaxe dos scripts de compilação SCons e bundle para MAC para ficarem compatíveis com a versão 4 do SCons
- Portado para **Python 3** e **c++ 11**
- Binários de **64 bits** (@todo podendo ser ajustado para saída **32 bits**)

## Compilação
1. Clone o SDK:
  ```shell
  git clone https://github.com/rdeprera/et-linux-sdk.git --depth 1 --branch master
  cd et-linux-sdk/src
  ```
2. Instale as dependências compiladores (normalmente gcc e g++), SCons e Python 3. No Debian:
  ```shell
  sudo apt install gcc g++ scons python3 -y
  ```
3. Use o SCons para fazer a compilação, exemplo:
  ```shell
  cons BUILD=release BUILDMPBIN=1 COPYBINS=1 NOCONF=1
  ```

### Parâmetros para Compilação usando o SCons
```shell
Usage: scons [OPTIONS] [TARGET] [CONFIG]

[OPTIONS] and [TARGET] are covered in command line options, use scons -H

[CONFIG]: KEY="VALUE" [...]
a number of configuration options saved between runs in the """ + conf_filename + """ file
erase """ + conf_filename + """ to start with default settings again

CC (default gcc)
CXX (default g++)
	Specify C and C++ compilers (defaults gcc and g++)
	ex: CC="gcc-3.3"
	You can use ccache and distcc, for instance:
	CC="ccache distcc gcc" CXX="ccache distcc g++"

JOBS (default 1)
	Parallel build

BUILD (default debug)
	Use debug-all/debug/release to select build settings
	ex: BUILD="release"
	debug-all: no optimisations, debugging symbols
	debug: -O -g
	release: all optimisations, including CPU target etc.
	
DEDICATED (default 2)
	Control regular / dedicated type of build:
	0 - client
	1 - dedicated server
	2 - both

TARGET_GAME (default 1)
	Build game module

TARGET_CGAME (default 1)
	Build cgame module

TARGET_UI (default 1)
	Build ui module

BUILD_ROOT (default 'build')
	change the build root directory
	
NOCONF (default 0, not saved)
	ignore site configuration and use defaults + command line only

COPYBINS (default 0, not saved)
	copy the binaries in a ready-to-release format

BUILDMPBIN (default 0, not saved)
	build mp_bin.pk3 using bin/ directories and game binaries for all platforms

BUILDBUNDLE (default 0, not saved)
	create mac bundle files
```
