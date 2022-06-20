Conan Workspace setup for local development

# Add remotes
conan remote add traact-camposs https://conan.campar.in.tum.de/api/conan/conan-traact true
conan remote add camposs https://conan.campar.in.tum.de/api/conan/conan-camposs true


# Installation

git clone https://github.com/traact/traact_clean_workspace.git my_workspace
cd my_workspace

# clone all traact libraries you want to edit e.g.

git clone https://github.com/traact/traact_core.git
git clone https://github.com/traact/traact_spatial.git

# edit conanws.yml and add the libraries to the editables

'''
editables:
traact_core/0.0.2@camposs/stable:
path: traact_core    
traact_run_env/1.0.0@camposs/stable:
path: traact_run_env
layout: layout_no_lib
root: traact_core/0.0.2@camposs/stable
'''

# create build directory (e.g. for debug: cmake-build-debug, release: cmake-build-release )

'''
mkdir cmake-build-debug
cd cmake-build-debug
'''

# build workspace (using a matching profile e.g. debug/release)

# use --profile=my_profile to specify the conan profile to use

'''
conan workspace install .. --profile debug
'''

# Generate project files, use your compiler

# Linux

'''
cmake .. -DCMAKE_BUILD_TYPE=Debug
'''
