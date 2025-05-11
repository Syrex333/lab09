user@Syrex:~$ export GITHUB_USERNAME=Syrex333
user@Syrex:~$ cd ${GITHUB_USERNAME}/workspace
user@Syrex:~/Syrex333/workspace$ pushd .
~/Syrex333/workspace ~/Syrex333/workspace
user@Syrex:~/Syrex333/workspace$ source scripts/activate
user@Syrex:~/Syrex333/workspace$ git clone https://github.com/${GITHUB_USERNAME}/lab07 lab08
Cloning into 'lab08'...
remote: Enumerating objects: 255, done.
remote: Counting objects: 100% (255/255), done.
remote: Compressing objects: 100% (120/120), done.
remote: Total 255 (delta 101), reused 255 (delta 101), pack-reused 0 (from 0)
Receiving objects: 100% (255/255), 956.75 KiB | 3.43 MiB/s, done.
Resolving deltas: 100% (101/101), done.
user@Syrex:~/Syrex333/workspace$ cd lab08
user@Syrex:~/Syrex333/workspace/lab08$ git submodule update --init
Submodule 'tools/polly' (https://github.com/ruslo/polly) registered for path 'tools/polly'
Cloning into '/home/user/Syrex333/workspace/lab08/tools/polly'...
Submodule path 'tools/polly': checked out 'ef7e79c2c297d456f2742fd0b976f555d058d4e0'
user@Syrex:~/Syrex333/workspace/lab08$ git remote remove origin
user@Syrex:~/Syrex333/workspace/lab08$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab08
user@Syrex:~/Syrex333/workspace/lab08$ cat > Dockerfile <<EOF
> FROM ubuntu:18.04
> EOF
user@Syrex:~/Syrex333/workspace/lab08$ cat >> Dockerfile <<EOF
> RUN apt update
> RUN apt install -yy gcc g++ cmake
> EOF
user@Syrex:~/Syrex333/workspace/lab08$ cat >> Dockerfile <<EOF
> COPY . print/
> WORKDIR print
> EOF
user@Syrex:~/Syrex333/workspace/lab08$ cat >> Dockerfile <<EOF
> RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
> RUN cmake --build _build
> RUN cmake --build _build --target install
> EOF
user@Syrex:~/Syrex333/workspace/lab08$ cat >> Dockerfile <<EOF
> ENV LOG_PATH /home/logs/log.txt
> EOF
user@Syrex:~/Syrex333/workspace/lab08$ cat >> Dockerfile <<EOF
> VOLUME /home/logs
> EOF
user@Syrex:~/Syrex333/workspace/lab08$ cat >> Dockerfile <<EOF
> WORKDIR _install/bin
> EOF
user@Syrex:~/Syrex333/workspace/lab08$ cat >> Dockerfile <<EOF
> ENTRYPOINT ./demo
> EOF
user@Syrex:~/Syrex333/workspace/lab08$ docker build -t logger .
ERROR: permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Head "http://%2Fvar%2Frun%2Fdocker.sock/_ping": dial unix /var/run/docker.sock: connect: permission denied
user@Syrex:~/Syrex333/workspace/lab08$ sudo docker build -t logger .
[sudo] password for user:
[+] Building 38.4s (10/13)                                                                               docker:default
 => [internal] load build definition from Dockerfile                                                               0.0s
 => => transferring dockerfile: 372B                                                                               0.0s
 => [internal] load metadata for docker.io/library/ubuntu:18.04                                                    1.4s
 => [internal] load .dockerignore                                                                                  0.0s
 => => transferring context: 2B                                                                                    0.0s
 => [1/9] FROM docker.io/library/ubuntu:18.04@sha256:152dc042452c496007f07ca9127571cb9c29697f42acbfad72324b2bb2e4  0.0s
 => [internal] load build context                                                                                  0.3s
 => => transferring context: 9.13MB                                                                                0.3s
 => CACHED [2/9] RUN apt update                                                                                    0.0s
 => CACHED [3/9] RUN apt install -yy gcc g++ cmake                                                                 0.0s
 => [4/9] COPY . print/                                                                                            0.3s
 => [5/9] WORKDIR print                                                                                            0.0s
 => ERROR [6/9] RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install                 36.3s
------
 > [6/9] RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install:
0.601 -- [hunter] Initializing Hunter workspace (23f1b5a0acffae50fda423388c843a8e7b6e1eb0)
0.601 -- [hunter]   https://github.com/cpp-pm/hunter/archive/v0.23.308.tar.gz
0.601 -- [hunter]   -> /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a
3.402 -- The C compiler identification is GNU 7.5.0
3.565 -- The CXX compiler identification is GNU 7.5.0
3.576 -- Check for working C compiler: /usr/bin/cc
3.675 -- Check for working C compiler: /usr/bin/cc -- works
3.677 -- Detecting C compiler ABI info
3.773 -- Detecting C compiler ABI info - done
3.778 -- Detecting C compile features
4.080 -- Detecting C compile features - done
4.085 -- Check for working CXX compiler: /usr/bin/c++
4.196 -- Check for working CXX compiler: /usr/bin/c++ -- works
4.197 -- Detecting CXX compiler ABI info
4.305 -- Detecting CXX compiler ABI info - done
4.310 -- Detecting CXX compile features
4.788 -- Detecting CXX compile features - done
4.791 -- [hunter] Calculating Toolchain-SHA1
6.187 -- [hunter] Calculating Config-SHA1
6.309 -- [hunter] HUNTER_ROOT: /root/.hunter
6.309 -- [hunter] [ Hunter-ID: 23f1b5a | Toolchain-ID: 9b2c9d4 | Config-ID: bf2be25 ]
6.404 -- [hunter] GTEST_ROOT: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Install (ver.: 1.11.0)
6.991 -- [hunter] Building GTest
7.009 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/cache.cmake
7.009 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/args.cmake
7.068 -- The C compiler identification is GNU 7.5.0
7.131 -- The CXX compiler identification is GNU 7.5.0
7.136 -- Check for working C compiler: /usr/bin/cc
7.209 -- Check for working C compiler: /usr/bin/cc -- works
7.210 -- Detecting C compile features
7.448 -- Detecting C compile features - done
7.451 -- Check for working CXX compiler: /usr/bin/c++
7.541 -- Check for working CXX compiler: /usr/bin/c++ -- works
7.542 -- Detecting CXX compile features
7.977 -- Detecting CXX compile features - done
8.034 -- Configuring done
8.039 -- Generating done
8.040 -- Build files have been written to: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Build
8.093 Scanning dependencies of target GTest-Release
8.107 [  6%] Creating directories for 'GTest-Release'
8.179 [ 12%] Performing download step (download, verify and extract) for 'GTest-Release'
8.196 -- Downloading...
8.196    dst='/root/.hunter/_Base/Download/GTest/1.11.0/7b100bb/release-1.11.0.tar.gz'
8.196    timeout='none'
8.196 -- Using src='https://github.com/google/googletest/archive/release-1.11.0.tar.gz'
13.41 -- verifying file...
13.41        file='/root/.hunter/_Base/Download/GTest/1.11.0/7b100bb/release-1.11.0.tar.gz'
13.41 -- Downloading... done
13.45 -- extracting...
13.45      src='/root/.hunter/_Base/Download/GTest/1.11.0/7b100bb/release-1.11.0.tar.gz'
13.45      dst='/root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Source'
13.45 -- extracting... [tar xfz]
13.51 -- extracting... [analysis]
13.51 -- extracting... [rename]
13.51 -- extracting... [clean up]
13.51 -- extracting... done
13.55 [ 18%] No patch step for 'GTest-Release'
13.59 [ 25%] No update step for 'GTest-Release'
13.64 [ 31%] Performing configure step for 'GTest-Release'
13.66 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/cache.cmake
13.66 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/args.cmake
13.73 -- The C compiler identification is GNU 7.5.0
13.81 -- The CXX compiler identification is GNU 7.5.0
13.81 -- Check for working C compiler: /usr/bin/cc
13.93 -- Check for working C compiler: /usr/bin/cc -- works
13.93 -- Detecting C compile features
14.29 -- Detecting C compile features - done
14.29 -- Check for working CXX compiler: /usr/bin/c++
14.41 -- Check for working CXX compiler: /usr/bin/c++ -- works
14.41 -- Detecting CXX compile features
14.98 -- Detecting CXX compile features - done
15.00 -- Could NOT find PythonInterp (missing: PYTHON_EXECUTABLE)
15.00 -- Looking for pthread.h
15.13 -- Looking for pthread.h - found
15.13 -- Looking for pthread_create
15.24 -- Looking for pthread_create - not found
15.24 -- Looking for pthread_create in pthreads
15.34 -- Looking for pthread_create in pthreads - not found
15.34 -- Looking for pthread_create in pthread
15.45 -- Looking for pthread_create in pthread - found
15.45 -- Found Threads: TRUE
15.46 -- Configuring done
15.48 -- Generating done
15.49 -- Build files have been written to: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Build/GTest-Release-prefix/src/GTest-Release-build
15.51 [ 37%] Performing build step for 'GTest-Release'
15.58 Scanning dependencies of target gtest
15.60 [ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
22.53 [ 25%] Linking CXX static library ../lib/libgtest.a
22.58 [ 25%] Built target gtest
22.59 Scanning dependencies of target gtest_main
22.60 Scanning dependencies of target gmock
22.61 [ 37%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
22.61 [ 50%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
23.22 [ 62%] Linking CXX static library ../lib/libgtest_main.a
23.25 [ 62%] Built target gtest_main
24.98 [ 75%] Linking CXX static library ../lib/libgmock.a
25.02 [ 75%] Built target gmock
25.05 Scanning dependencies of target gmock_main
25.06 [ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
25.90 [100%] Linking CXX static library ../lib/libgmock_main.a
25.94 [100%] Built target gmock_main
25.97 [ 43%] Performing install step for 'GTest-Release'
26.03 [ 25%] Built target gtest
26.06 [ 50%] Built target gmock
26.09 [ 75%] Built target gmock_main
26.11 [100%] Built target gtest_main
26.13 Install the project...
26.14 -- Install configuration: "Release"
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-spec-builders.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-more-actions.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-matchers.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/gmock-port.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/README.md
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/gmock-pp.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-actions.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-function-mocker.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-cardinalities.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-more-matchers.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-nice-strict.h
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgmock.a
26.14 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgmock_main.a
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gmock.pc
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gmock_main.pc
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestTargets.cmake
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestTargets-release.cmake
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestConfigVersion.cmake
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestConfig.cmake
26.15 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-typed-test.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-param-test.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-test-part.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-spi.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest_prod.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest_pred_impl.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-string.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-internal.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-port.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/gtest.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/README.md
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-printers.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-matchers.h
26.15 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-message.h
26.16 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-death-test.h
26.16 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgtest.a
26.16 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgtest_main.a
26.16 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gtest.pc
26.16 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gtest_main.pc
26.17 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/args.cmake
26.19 [ 50%] Completed 'GTest-Release'
26.24 [ 50%] Built target GTest-Release
26.25 Scanning dependencies of target GTest-Debug
26.26 [ 56%] Creating directories for 'GTest-Debug'
26.34 [ 62%] Performing download step (download, verify and extract) for 'GTest-Debug'
26.36 -- verifying file...
26.36        file='/root/.hunter/_Base/Download/GTest/1.11.0/7b100bb/release-1.11.0.tar.gz'
26.36 -- File already exists and hash match (skip download):
26.36   file='/root/.hunter/_Base/Download/GTest/1.11.0/7b100bb/release-1.11.0.tar.gz'
26.36   SHA1='7b100bb68db8df1060e178c495f3cbe941c9b058'
26.38 -- extracting...
26.38      src='/root/.hunter/_Base/Download/GTest/1.11.0/7b100bb/release-1.11.0.tar.gz'
26.38      dst='/root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Source'
26.38 -- extracting... [tar xfz]
26.42 -- extracting... [analysis]
26.42 -- extracting... [rename]
26.43 -- extracting... [clean up]
26.43 -- extracting... done
26.45 [ 68%] No patch step for 'GTest-Debug'
26.49 [ 75%] No update step for 'GTest-Debug'
26.51 [ 81%] Performing configure step for 'GTest-Debug'
26.52 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/cache.cmake
26.52 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/args.cmake
26.57 -- The C compiler identification is GNU 7.5.0
26.63 -- The CXX compiler identification is GNU 7.5.0
26.64 -- Check for working C compiler: /usr/bin/cc
26.73 -- Check for working C compiler: /usr/bin/cc -- works
26.73 -- Detecting C compile features
26.99 -- Detecting C compile features - done
26.99 -- Check for working CXX compiler: /usr/bin/c++
27.08 -- Check for working CXX compiler: /usr/bin/c++ -- works
27.08 -- Detecting CXX compile features
27.44 -- Detecting CXX compile features - done
27.44 -- Could NOT find PythonInterp (missing: PYTHON_EXECUTABLE)
27.45 -- Looking for pthread.h
27.51 -- Looking for pthread.h - found
27.51 -- Looking for pthread_create
27.58 -- Looking for pthread_create - not found
27.58 -- Looking for pthread_create in pthreads
27.64 -- Looking for pthread_create in pthreads - not found
27.64 -- Looking for pthread_create in pthread
27.71 -- Looking for pthread_create in pthread - found
27.71 -- Found Threads: TRUE
27.72 -- Configuring done
27.73 -- Generating done
27.74 -- Build files have been written to: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Build/GTest-Debug-prefix/src/GTest-Debug-build
27.76 [ 87%] Performing build step for 'GTest-Debug'
27.81 Scanning dependencies of target gtest
27.82 [ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
31.74 [ 25%] Linking CXX static library ../lib/libgtestd.a
31.82 [ 25%] Built target gtest
31.84 Scanning dependencies of target gtest_main
31.84 Scanning dependencies of target gmock
31.85 [ 37%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
31.85 [ 50%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
32.57 [ 62%] Linking CXX static library ../lib/libgtest_maind.a
32.60 [ 62%] Built target gtest_main
33.64 [ 75%] Linking CXX static library ../lib/libgmockd.a
33.71 [ 75%] Built target gmock
33.73 Scanning dependencies of target gmock_main
33.74 [ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
34.75 [100%] Linking CXX static library ../lib/libgmock_maind.a
34.79 [100%] Built target gmock_main
34.82 [ 93%] Performing install step for 'GTest-Debug'
34.88 [ 25%] Built target gtest
34.91 [ 50%] Built target gmock
34.93 [ 75%] Built target gmock_main
34.96 [100%] Built target gtest_main
34.98 Install the project...
34.99 -- Install configuration: "Debug"
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-spec-builders.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-more-actions.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-matchers.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/gmock-port.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/README.md
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/gmock-pp.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-actions.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-function-mocker.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-cardinalities.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-more-matchers.h
34.99 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-nice-strict.h
34.99 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgmockd.a
34.99 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgmock_maind.a
35.00 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gmock.pc
35.00 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gmock_main.pc
35.00 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestTargets.cmake
35.00 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestTargets-debug.cmake
35.00 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestConfigVersion.cmake
35.00 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestConfig.cmake
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-typed-test.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-param-test.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-test-part.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-spi.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest_prod.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest_pred_impl.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-string.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-internal.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-port.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/gtest.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/README.md
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-printers.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-matchers.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-message.h
35.00 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-death-test.h
35.00 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgtestd.a
35.01 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgtest_maind.a
35.01 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gtest.pc
35.01 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gtest_main.pc
35.02 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/args.cmake
35.04 [100%] Completed 'GTest-Debug'
35.08 [100%] Built target GTest-Debug
35.10 -- [hunter] Build step successful (dir: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest)
35.97 -- [hunter] Cache saved: /root/.hunter/_Base/Cache/raw/8fd7e57d85eefa2dc455768767ef9885ae37ca59.tar.bz2
36.25
36.25 [hunter ** INTERNAL **] Link script failed: 1, , CMake Error at /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/scripts/link-all.cmake:1 (cmake_minimum_required):
36.25   CMake 3.12 or higher is required.  You are running version 3.10.2
36.25
36.25
36.25
36.25 [hunter ** INTERNAL **] [Directory:/root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/projects/GTest]
36.25
36.25 ------------------------------ ERROR -----------------------------
36.25     https://hunter.readthedocs.io/en/latest/reference/errors/error.internal.html
36.25 ------------------------------------------------------------------
36.25
36.25 CMake Error at /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/modules/hunter_error_page.cmake:12 (message):
36.25 Call Stack (most recent call first):
36.25   /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/modules/hunter_internal_error.cmake:13 (hunter_error_page)
36.25   /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/modules/hunter_unpack_directory.cmake:153 (hunter_internal_error)
36.25   /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/modules/hunter_save_to_cache.cmake:103 (hunter_unpack_directory)
36.25   /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/modules/hunter_download.cmake:635 (hunter_save_to_cache)
36.25   /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/projects/GTest/hunter.cmake:302 (hunter_download)
36.25   /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
36.25   CMakeLists.txt:24 (hunter_add_package)
36.25
36.25
36.25 -- Configuring incomplete, errors occurred!
36.25 See also "/print/_build/CMakeFiles/CMakeOutput.log".
------

 3 warnings found (use docker --debug to expand):
 - WorkdirRelativePath: Relative workdir "print" can have unexpected results if the base image changes (line 5)
 - LegacyKeyValueFormat: "ENV key=value" should be used instead of legacy "ENV key value" format (line 9)
 - JSONArgsRecommended: JSON arguments recommended for ENTRYPOINT to prevent unintended behavior related to OS signals (line 12)
Dockerfile:6
--------------------
   4 |     COPY . print/
   5 |     WORKDIR print
   6 | >>> RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
   7 |     RUN cmake --build _build
   8 |     RUN cmake --build _build --target install
--------------------
ERROR: failed to solve: process "/bin/sh -c cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install" did not complete successfully: exit code: 1
user@Syrex:~/Syrex333/workspace/lab08$ cd
user@Syrex:~$ cd ~/Syrex333/workspace/lab08
user@Syrex:~/Syrex333/workspace/lab08$ ls
 CMakeLists.txt      Dockerfile   cmake      include                 tests
 CPackConfig.cmake   LICENSE      demo      'procedure of actions'   text
 ChangeLog.md        README.md    examples   report                 'the order of execution of commands'
 DESCRIPTION         _builds      file.txt   sources                 tools
user@Syrex:~/Syrex333/workspace/lab08$ cd cmake
user@Syrex:~/Syrex333/workspace/lab08/cmake$ ls
Hunter  HunterGate.cmake
user@Syrex:~/Syrex333/workspace/lab08/cmake$ nano HunterGate.cmake
user@Syrex:~/Syrex333/workspace/lab08/cmake$ cd ..
user@Syrex:~/Syrex333/workspace/lab08$ sudo docker build -t logger .
[+] Building 31.8s (10/13)                                                                               docker:default
 => [internal] load build definition from Dockerfile                                                               0.0s
 => => transferring dockerfile: 372B                                                                               0.0s
 => [internal] load metadata for docker.io/library/ubuntu:18.04                                                    0.5s
 => [internal] load .dockerignore                                                                                  0.0s
 => => transferring context: 2B                                                                                    0.0s
 => [1/9] FROM docker.io/library/ubuntu:18.04@sha256:152dc042452c496007f07ca9127571cb9c29697f42acbfad72324b2bb2e4  0.0s
 => [internal] load build context                                                                                  0.1s
 => => transferring context: 91.70kB                                                                               0.1s
 => CACHED [2/9] RUN apt update                                                                                    0.0s
 => CACHED [3/9] RUN apt install -yy gcc g++ cmake                                                                 0.0s
 => CACHED [4/9] COPY . print/                                                                                     0.0s
 => CACHED [5/9] WORKDIR print                                                                                     0.0s
 => ERROR [6/9] RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install                 31.1s
------
 > [6/9] RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install:
0.454 -- [hunter] Initializing Hunter workspace (23f1b5a0acffae50fda423388c843a8e7b6e1eb0)
0.454 -- [hunter]   https://github.com/cpp-pm/hunter/archive/v0.23.308.tar.gz
0.454 -- [hunter]   -> /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a
2.868 -- The C compiler identification is GNU 7.5.0
2.942 -- The CXX compiler identification is GNU 7.5.0
2.946 -- Check for working C compiler: /usr/bin/cc
3.055 -- Check for working C compiler: /usr/bin/cc -- works
3.055 -- Detecting C compiler ABI info
3.150 -- Detecting C compiler ABI info - done
3.155 -- Detecting C compile features
3.467 -- Detecting C compile features - done
3.470 -- Check for working CXX compiler: /usr/bin/c++
3.573 -- Check for working CXX compiler: /usr/bin/c++ -- works
3.575 -- Detecting CXX compiler ABI info
3.711 -- Detecting CXX compiler ABI info - done
3.715 -- Detecting CXX compile features
4.140 -- Detecting CXX compile features - done
4.143 -- [hunter] Calculating Toolchain-SHA1
5.578 -- [hunter] Calculating Config-SHA1
5.698 -- [hunter] HUNTER_ROOT: /root/.hunter
5.698 -- [hunter] [ Hunter-ID: 23f1b5a | Toolchain-ID: 9b2c9d4 | Config-ID: bf2be25 ]
5.790 -- [hunter] GTEST_ROOT: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Install (ver.: 1.11.0)
6.157 -- [hunter] Building GTest
6.174 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/cache.cmake
6.174 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/args.cmake
6.239 -- The C compiler identification is GNU 7.5.0
6.305 -- The CXX compiler identification is GNU 7.5.0
6.310 -- Check for working C compiler: /usr/bin/cc
6.406 -- Check for working C compiler: /usr/bin/cc -- works
6.407 -- Detecting C compile features
6.686 -- Detecting C compile features - done
6.695 -- Check for working CXX compiler: /usr/bin/c++
6.797 -- Check for working CXX compiler: /usr/bin/c++ -- works
6.798 -- Detecting CXX compile features
7.220 -- Detecting CXX compile features - done
7.276 -- Configuring done
7.282 -- Generating done
7.284 -- Build files have been written to: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Build
7.340 Scanning dependencies of target GTest-Release
7.361 [  6%] Creating directories for 'GTest-Release'
7.444 [ 12%] Performing download step (download, verify and extract) for 'GTest-Release'
7.458 -- Downloading...
7.458    dst='/root/.hunter/_Base/Download/GTest/1.11.0/7b100bb/release-1.11.0.tar.gz'
7.458    timeout='none'
7.458 -- Using src='https://github.com/google/googletest/archive/release-1.11.0.tar.gz'
8.504 -- verifying file...
8.504        file='/root/.hunter/_Base/Download/GTest/1.11.0/7b100bb/release-1.11.0.tar.gz'
8.506 -- Downloading... done
8.543 -- extracting...
8.543      src='/root/.hunter/_Base/Download/GTest/1.11.0/7b100bb/release-1.11.0.tar.gz'
8.543      dst='/root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Source'
8.543 -- extracting... [tar xfz]
8.589 -- extracting... [analysis]
8.589 -- extracting... [rename]
8.590 -- extracting... [clean up]
8.590 -- extracting... done
8.618 [ 18%] No patch step for 'GTest-Release'
8.658 [ 25%] No update step for 'GTest-Release'
8.691 [ 31%] Performing configure step for 'GTest-Release'
8.702 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/cache.cmake
8.702 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/args.cmake
8.764 -- The C compiler identification is GNU 7.5.0
8.831 -- The CXX compiler identification is GNU 7.5.0
8.836 -- Check for working C compiler: /usr/bin/cc
8.927 -- Check for working C compiler: /usr/bin/cc -- works
8.927 -- Detecting C compile features
9.189 -- Detecting C compile features - done
9.194 -- Check for working CXX compiler: /usr/bin/c++
9.297 -- Check for working CXX compiler: /usr/bin/c++ -- works
9.298 -- Detecting CXX compile features
9.727 -- Detecting CXX compile features - done
9.738 -- Could NOT find PythonInterp (missing: PYTHON_EXECUTABLE)
9.741 -- Looking for pthread.h
9.832 -- Looking for pthread.h - found
9.833 -- Looking for pthread_create
9.917 -- Looking for pthread_create - not found
9.918 -- Looking for pthread_create in pthreads
9.995 -- Looking for pthread_create in pthreads - not found
9.996 -- Looking for pthread_create in pthread
10.09 -- Looking for pthread_create in pthread - found
10.09 -- Found Threads: TRUE
10.10 -- Configuring done
10.12 -- Generating done
10.12 -- Build files have been written to: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Build/GTest-Release-prefix/src/GTest-Release-build
10.15 [ 37%] Performing build step for 'GTest-Release'
10.21 Scanning dependencies of target gtest
10.23 [ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
17.26 [ 25%] Linking CXX static library ../lib/libgtest.a
17.32 [ 25%] Built target gtest
17.34 Scanning dependencies of target gtest_main
17.35 Scanning dependencies of target gmock
17.35 [ 37%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
17.36 [ 50%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
17.99 [ 62%] Linking CXX static library ../lib/libgtest_main.a
18.02 [ 62%] Built target gtest_main
19.72 [ 75%] Linking CXX static library ../lib/libgmock.a
19.76 [ 75%] Built target gmock
19.78 Scanning dependencies of target gmock_main
19.80 [ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
20.67 [100%] Linking CXX static library ../lib/libgmock_main.a
20.71 [100%] Built target gmock_main
20.75 [ 43%] Performing install step for 'GTest-Release'
20.82 [ 25%] Built target gtest
20.84 [ 50%] Built target gmock
20.87 [ 75%] Built target gmock_main
20.89 [100%] Built target gtest_main
20.92 Install the project...
20.93 -- Install configuration: "Release"
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-spec-builders.h
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-more-actions.h
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-matchers.h
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/gmock-port.h
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/README.md
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/gmock-pp.h
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-actions.h
20.93 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-function-mocker.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-cardinalities.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-more-matchers.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-nice-strict.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgmock.a
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgmock_main.a
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gmock.pc
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gmock_main.pc
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestTargets.cmake
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestTargets-release.cmake
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestConfigVersion.cmake
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestConfig.cmake
20.94 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-typed-test.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-param-test.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-test-part.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-spi.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest_prod.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest_pred_impl.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-string.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-internal.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-port.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/gtest.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/README.md
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
20.94 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-printers.h
20.95 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-matchers.h
20.95 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-message.h
20.95 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-death-test.h
20.95 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgtest.a
20.95 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgtest_main.a
20.95 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gtest.pc
20.95 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gtest_main.pc
20.96 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/args.cmake
20.98 [ 50%] Completed 'GTest-Release'
21.02 [ 50%] Built target GTest-Release
21.04 Scanning dependencies of target GTest-Debug
21.06 [ 56%] Creating directories for 'GTest-Debug'
21.14 [ 62%] Performing download step (download, verify and extract) for 'GTest-Debug'
21.16 -- verifying file...
21.16        file='/root/.hunter/_Base/Download/GTest/1.11.0/7b100bb/release-1.11.0.tar.gz'
21.16 -- File already exists and hash match (skip download):
21.16   file='/root/.hunter/_Base/Download/GTest/1.11.0/7b100bb/release-1.11.0.tar.gz'
21.16   SHA1='7b100bb68db8df1060e178c495f3cbe941c9b058'
21.19 -- extracting...
21.19      src='/root/.hunter/_Base/Download/GTest/1.11.0/7b100bb/release-1.11.0.tar.gz'
21.19      dst='/root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Source'
21.19 -- extracting... [tar xfz]
21.23 -- extracting... [analysis]
21.23 -- extracting... [rename]
21.24 -- extracting... [clean up]
21.24 -- extracting... done
21.26 [ 68%] No patch step for 'GTest-Debug'
21.29 [ 75%] No update step for 'GTest-Debug'
21.31 [ 81%] Performing configure step for 'GTest-Debug'
21.33 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/cache.cmake
21.33 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/args.cmake
21.38 -- The C compiler identification is GNU 7.5.0
21.44 -- The CXX compiler identification is GNU 7.5.0
21.45 -- Check for working C compiler: /usr/bin/cc
21.54 -- Check for working C compiler: /usr/bin/cc -- works
21.54 -- Detecting C compile features
21.79 -- Detecting C compile features - done
21.79 -- Check for working CXX compiler: /usr/bin/c++
21.87 -- Check for working CXX compiler: /usr/bin/c++ -- works
21.87 -- Detecting CXX compile features
22.21 -- Detecting CXX compile features - done
22.22 -- Could NOT find PythonInterp (missing: PYTHON_EXECUTABLE)
22.22 -- Looking for pthread.h
22.30 -- Looking for pthread.h - found
22.30 -- Looking for pthread_create
22.40 -- Looking for pthread_create - not found
22.40 -- Looking for pthread_create in pthreads
22.47 -- Looking for pthread_create in pthreads - not found
22.47 -- Looking for pthread_create in pthread
22.56 -- Looking for pthread_create in pthread - found
22.56 -- Found Threads: TRUE
22.57 -- Configuring done
22.58 -- Generating done
22.58 -- Build files have been written to: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Build/GTest-Debug-prefix/src/GTest-Debug-build
22.61 [ 87%] Performing build step for 'GTest-Debug'
22.67 Scanning dependencies of target gtest
22.70 [ 12%] Building CXX object googletest/CMakeFiles/gtest.dir/src/gtest-all.cc.o
26.58 [ 25%] Linking CXX static library ../lib/libgtestd.a
26.67 [ 25%] Built target gtest
26.68 Scanning dependencies of target gtest_main
26.68 Scanning dependencies of target gmock
26.69 [ 37%] Building CXX object googletest/CMakeFiles/gtest_main.dir/src/gtest_main.cc.o
26.70 [ 50%] Building CXX object googlemock/CMakeFiles/gmock.dir/src/gmock-all.cc.o
27.37 [ 62%] Linking CXX static library ../lib/libgtest_maind.a
27.41 [ 62%] Built target gtest_main
28.37 [ 75%] Linking CXX static library ../lib/libgmockd.a
28.43 [ 75%] Built target gmock
28.45 Scanning dependencies of target gmock_main
28.46 [ 87%] Building CXX object googlemock/CMakeFiles/gmock_main.dir/src/gmock_main.cc.o
29.44 [100%] Linking CXX static library ../lib/libgmock_maind.a
29.48 [100%] Built target gmock_main
29.51 [ 93%] Performing install step for 'GTest-Debug'
29.57 [ 25%] Built target gtest
29.61 [ 50%] Built target gmock
29.63 [ 75%] Built target gmock_main
29.66 [100%] Built target gtest_main
29.68 Install the project...
29.69 -- Install configuration: "Debug"
29.69 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include
29.69 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock
29.69 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-spec-builders.h
29.69 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-more-actions.h
29.69 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-matchers.h
29.69 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal
29.69 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/gmock-internal-utils.h
29.69 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/gmock-port.h
29.69 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/gmock-generated-actions.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/gmock-port.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/gmock-matchers.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/custom/README.md
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/internal/gmock-pp.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-actions.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-function-mocker.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-cardinalities.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-more-matchers.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gmock/gmock-nice-strict.h
29.70 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgmockd.a
29.70 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgmock_maind.a
29.70 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gmock.pc
29.70 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gmock_main.pc
29.70 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestTargets.cmake
29.70 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestTargets-debug.cmake
29.70 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestConfigVersion.cmake
29.70 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/cmake/GTest/GTestConfig.cmake
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-typed-test.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-param-test.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-test-part.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-spi.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest_prod.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest_pred_impl.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-string.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-internal.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-death-test-internal.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-port-arch.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-port.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/gtest-port.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/gtest.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/gtest-printers.h
29.70 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/custom/README.md
29.71 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-param-util.h
29.71 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-type-util.h
29.71 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/internal/gtest-filepath.h
29.71 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-printers.h
29.71 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-matchers.h
29.71 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-message.h
29.71 -- Up-to-date: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/include/gtest/gtest-death-test.h
29.71 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgtestd.a
29.72 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/libgtest_maind.a
29.72 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gtest.pc
29.72 -- Installing: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/Install/lib/pkgconfig/gtest_main.pc
29.73 loading initial cache file /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest/args.cmake
29.75 [100%] Completed 'GTest-Debug'
29.79 [100%] Built target GTest-Debug
29.81 -- [hunter] Build step successful (dir: /root/.hunter/_Base/23f1b5a/9b2c9d4/bf2be25/Build/GTest)
30.68 -- [hunter] Cache saved: /root/.hunter/_Base/Cache/raw/06c42513d422ca2da38313bbf49199f9d9d0c4f2.tar.bz2
30.98
30.98 [hunter ** INTERNAL **] Link script failed: 1, , CMake Error at /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/scripts/link-all.cmake:1 (cmake_minimum_required):
30.98   CMake 3.12 or higher is required.  You are running version 3.10.2
30.98
30.98
30.98
30.98 [hunter ** INTERNAL **] [Directory:/root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/projects/GTest]
30.98
30.98 ------------------------------ ERROR -----------------------------
30.98     https://hunter.readthedocs.io/en/latest/reference/errors/error.internal.html
30.98 ------------------------------------------------------------------
30.98
30.98 CMake Error at /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/modules/hunter_error_page.cmake:12 (message):
30.98 Call Stack (most recent call first):
30.98   /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/modules/hunter_internal_error.cmake:13 (hunter_error_page)
30.98   /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/modules/hunter_unpack_directory.cmake:153 (hunter_internal_error)
30.98   /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/modules/hunter_save_to_cache.cmake:103 (hunter_unpack_directory)
30.98   /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/modules/hunter_download.cmake:635 (hunter_save_to_cache)
30.98   /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/projects/GTest/hunter.cmake:302 (hunter_download)
30.98   /root/.hunter/_Base/Download/Hunter/0.23.308/23f1b5a/Unpacked/cmake/modules/hunter_add_package.cmake:62 (include)
30.98   CMakeLists.txt:24 (hunter_add_package)
30.98
30.98
30.99 -- Configuring incomplete, errors occurred!
30.99 See also "/print/_build/CMakeFiles/CMakeOutput.log".
------

 3 warnings found (use docker --debug to expand):
 - WorkdirRelativePath: Relative workdir "print" can have unexpected results if the base image changes (line 5)
 - LegacyKeyValueFormat: "ENV key=value" should be used instead of legacy "ENV key value" format (line 9)
 - JSONArgsRecommended: JSON arguments recommended for ENTRYPOINT to prevent unintended behavior related to OS signals (line 12)
Dockerfile:6
--------------------
   4 |     COPY . print/
   5 |     WORKDIR print
   6 | >>> RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install
   7 |     RUN cmake --build _build
   8 |     RUN cmake --build _build --target install
--------------------
ERROR: failed to solve: process "/bin/sh -c cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install" did not complete successfully: exit code: 1
user@Syrex:~/Syrex333/workspace/lab08$ ls
 CMakeLists.txt      Dockerfile   cmake      include                 tests
 CPackConfig.cmake   LICENSE      demo      'procedure of actions'   text
 ChangeLog.md        README.md    examples   report                 'the order of execution of commands'
 DESCRIPTION         _builds      file.txt   sources                 tools
user@Syrex:~/Syrex333/workspace/lab08$ cd Dockerfile
-bash: cd: Dockerfile: Not a directory
user@Syrex:~/Syrex333/workspace/lab08$ nano Dockerfile
user@Syrex:~/Syrex333/workspace/lab08$ sudo docker build -t logger .
[+] Building 70.0s (10/10) FINISHED                                                                      docker:default
 => [internal] load build definition from Dockerfile                                                               0.0s
 => => transferring dockerfile: 604B                                                                               0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                   1.9s
 => [internal] load .dockerignore                                                                                  0.0s
 => => transferring context: 2B                                                                                    0.0s
 => [1/5] FROM docker.io/library/ubuntu:latest@sha256:6015f66923d7afbc53558d7ccffd325d43b4e249f41a6e93eef074c9505  3.6s
 => => resolve docker.io/library/ubuntu:latest@sha256:6015f66923d7afbc53558d7ccffd325d43b4e249f41a6e93eef074c9505  0.0s
 => => sha256:6015f66923d7afbc53558d7ccffd325d43b4e249f41a6e93eef074c9505d2233 6.69kB / 6.69kB                     0.0s
 => => sha256:dc17125eaac86538c57da886e494a34489122fb6a3ebb6411153d742594c2ddc 424B / 424B                         0.0s
 => => sha256:a0e45e2ce6e6e22e73185397d162a64fcf2f80a41c597015cab05d9a7b5913ce 2.30kB / 2.30kB                     0.0s
 => => sha256:0622fac788edde5d30e7bbd2688893e5452a19ff237a2e4615e2d8181321cb4e 29.72MB / 29.72MB                   1.6s
 => => extracting sha256:0622fac788edde5d30e7bbd2688893e5452a19ff237a2e4615e2d8181321cb4e                          1.7s
 => [internal] load build context                                                                                  0.1s
 => => transferring context: 75.03kB                                                                               0.1s
 => [2/5] RUN apt-get update &&     apt-get install -y cmake build-essential                                      28.1s
 => [3/5] COPY . /app/print                                                                                        0.2s
 => [4/5] WORKDIR /app/print                                                                                       0.0s
 => [5/5] RUN cmake -S . -B _build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install &&     cmake --bui  34.1s
 => exporting to image                                                                                             1.7s
 => => exporting layers                                                                                            1.7s
 => => writing image sha256:ff5c7678b13852d52f2f193561190d27c94b4ae46f8cd7b3335fb9c868e309f0                       0.0s
 => => naming to docker.io/library/logger                                                                          0.0s
user@Syrex:~/Syrex333/workspace/lab08$ docker images
permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Head "http://%2Fvar%2Frun%2Fdocker.sock/_ping": dial unix /var/run/docker.sock: connect: permission denied
user@Syrex:~/Syrex333/workspace/lab08$ sudo docker images
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
logger       latest    ff5c7678b138   16 seconds ago   572MB
user@Syrex:~/Syrex333/workspace/lab08$ mkdir logs
user@Syrex:~/Syrex333/workspace/lab08$ docker run -it -v "$(pwd)/logs/:/home/logs/" logger
docker: permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Head "http://%2Fvar%2Frun%2Fdocker.sock/_ping": dial unix /var/run/docker.sock: connect: permission denied.
See 'docker run --help'.
user@Syrex:~/Syrex333/workspace/lab08$ sudo docker run -it -v "$(pwd)/logs/:/home/logs/" logger
docker: Error response from daemon: failed to create task for container: failed to create shim task: OCI runtime create failed: runc create failed: unable to start container process: error during container init: exec: "your_executable": executable file not found in $PATH: unknown.
user@Syrex:~/Syrex333/workspace/lab08$ sudo docker run -it -v "$(pwd)/logs/:/home/logs/" logger /app/print/_install/bin/your_program_name
docker: Error response from daemon: failed to create task for container: failed to create shim task: OCI runtime create failed: runc create failed: unable to start container process: error during container init: exec: "your_executable": executable file not found in $PATH: unknown.
user@Syrex:~/Syrex333/workspace/lab08$ nano Dockerfile
user@Syrex:~/Syrex333/workspace/lab08$ sudo  docker build -t logger .
[+] Building 76.3s (5/10)                                                                                                      docker:default
[+] Building 76.3s (5/10)                                                                                                      docker:default
 => [internal] load build definition from Dockerfile                                                                                     0.0s
 => => transferring dockerfile: 629B                                                                                                     0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                         0.6s
 => [internal] load .dockerignore                                                                                                        0.0s0
 => => transferring context: 2B                                                                                                          0.0s
 => CACHED [1/6] FROM docker.io/library/ubuntu:latest@sha256:6015f66923d7afbc53558d7ccffd325d43b4e249f41a6e93eef074c9505d2233            0.0s
 => [internal] load build context                                                                                                        0.1s
 => => transferring context: 75.08kB                                                                                                     0.1s
 => [2/6] RUN apt-get update && apt-get install -y cmake build-essential                                                                75.7s
 => => # Preparing to unpack .../129-libldap-common_2.6.7+dfsg-1~exp1ubuntu8.2_all.deb ...
 => => # Unpacking libldap-common (2.6.7+dfsg-1~exp1ubuntu8.2) ...
 => => # Selecting previously unselected package libsasl2-modules:amd64.
 => => # Preparing to unpack .../130-libsasl2-modules_2.1.28+dfsg1-5ubuntu3.1_amd64.deb ...
 => => # Unpacking libsasl2-modules:amd64 (2.1.28+dfsg1-5ubuntu3.1) ...
 => => # Selecting previously unselected package manpages-dev.
Dockerfile:16
--------------------
  14 |
  15 |     # Проверяем, что файл существует
  16 | >>> RUN ls -la /app/print/_install/bin/
  17 |
  18 |     # Указываем точный путь к исполняемому файлу
--------------------
ERROR: failed to solve: process "/bin/sh -c ls -la /app/print/_install/bin/" did not complete successfully: exit code: 2
user@Syrex:~/Syrex333/workspace/lab08$ udo  docker build -t logger .

Command 'udo' not found, but can be installed with:

sudo apt install udo

user@Syrex:~/Syrex333/workspace/lab08$ sudo sudo  docker build -t logger .
[+] Building 1.6s (10/10) FINISHED                                                                                             docker:default
 => [internal] load build definition from Dockerfile                                                                                     0.0s
 => => transferring dockerfile: 629B                                                                                                     0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest                                                                         1.0s
 => [internal] load .dockerignore                                                                                                        0.0s
 => => transferring context: 2B                                                                                                          0.0s
 => [1/6] FROM docker.io/library/ubuntu:latest@sha256:6015f66923d7afbc53558d7ccffd325d43b4e249f41a6e93eef074c9505d2233                   0.0s
 => [internal] load build context                                                                                                        0.1s
 => => transferring context: 74.48kB                                                                                                     0.1s
 => CACHED [2/6] RUN apt-get update && apt-get install -y cmake build-essential                                                          0.0s
 => CACHED [3/6] COPY . /app/print                                                                                                       0.0s
 => CACHED [4/6] WORKDIR /app/print                                                                                                      0.0s
 => CACHED [5/6] RUN cmake -S . -B _build &&     cmake --build _build &&     cmake --build _build --target install                       0.0s
 => ERROR [6/6] RUN ls -la /app/print/_install/bin/                                                                                      0.4s
------
 > [6/6] RUN ls -la /app/print/_install/bin/:
0.354 ls: cannot access '/app/print/_install/bin/': No such file or directory
------
WARNING: current commit information was not captured by the build: failed to read current commit information with git rev-parse --is-inside-work-tree
Dockerfile:16
--------------------
  14 |
  15 |     # Проверяем, что файл существует
  16 | >>> RUN ls -la /app/print/_install/bin/
  17 |
  18 |     # Указываем точный путь к исполняемому файлу
--------------------
ERROR: failed to solve: process "/bin/sh -c ls -la /app/print/_install/bin/" did not complete successfully: exit code: 2
user@Syrex:~/Syrex333/workspace/lab08$ ls
 CMakeLists.txt      DESCRIPTION   README.md   demo       include                 report    text
 CPackConfig.cmake   Dockerfile    _builds     examples   logs                    sources  'the order of execution of commands'
 ChangeLog.md        LICENSE       cmake       file.txt  'procedure of actions'   tests     tools
user@Syrex:~/Syrex333/workspace/lab08$ nano Dockerfile
user@Syrex:~/Syrex333/workspace/lab08$ nano FROM ubuntu:20.04
 переменные окружения для избежания интерактивных запросов
ENV DEBIAN_FRONTEND=noninteractive
ENV TZ=Etc/UTC

user@Syrex:~/Syrex333/workspace/lab08$ nano Dockerfile
user@Syrex:~/Syrex333/workspace/lab08$ sudo  docker build -t logger .
[+] Building 87.9s (13/13) FINISHED                                                                                            docker:default
 => [internal] load build definition from Dockerfile                                                                                     0.0s
 => => transferring dockerfile: 963B                                                                                                     0.0s
 => [internal] load metadata for docker.io/library/ubuntu:20.04                                                                          2.0s
 => [internal] load .dockerignore                                                                                                        0.0s
 => => transferring context: 2B                                                                                                          0.0s
 => [1/8] FROM docker.io/library/ubuntu:20.04@sha256:8feb4d8ca5354def3d8fce243717141ce31e2c428701f6682bd2fafe15388214                    3.5s
 => => resolve docker.io/library/ubuntu:20.04@sha256:8feb4d8ca5354def3d8fce243717141ce31e2c428701f6682bd2fafe15388214                    0.0s
 => => sha256:8feb4d8ca5354def3d8fce243717141ce31e2c428701f6682bd2fafe15388214 6.69kB / 6.69kB                                           0.0s
 => => sha256:c664f8f86ed5a386b0a340d981b8f81714e21a8b9c73f658c4bea56aa179d54a 424B / 424B                                               0.0s
 => => sha256:b7bab04fd9aa0c771e5720bf0cc7cbf993fd6946645983d9096126e5af45d713 2.30kB / 2.30kB                                           0.0s
 => => sha256:13b7e930469f6d3575a320709035c6acf6f5485a76abcf03d1b92a64c09c2476 27.51MB / 27.51MB                                         1.5s
 => => extracting sha256:13b7e930469f6d3575a320709035c6acf6f5485a76abcf03d1b92a64c09c2476                                                1.7s
 => [internal] load build context                                                                                                        0.1s
 => => transferring context: 75.42kB                                                                                                     0.1s
 => [2/8] RUN apt-get update && apt-get install -y --no-install-recommends tzdata &&     ln -fs /usr/share/zoneinfo/Etc/UTC /etc/localt  7.8s
 => [3/8] RUN apt-get install -y     build-essential     cmake     git     wget     libssl-dev     ca-certificates     libgtest-dev     27.1s
 => [4/8] RUN rm -rf /root/.hunter                                                                                                       0.5s
 => [5/8] COPY . /print                                                                                                                  0.5s
 => [6/8] WORKDIR /print                                                                                                                 0.0s
 => [7/8] RUN cmake -H. -B_build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=_install                                             43.6s
 => [8/8] RUN cmake --build _build                                                                                                       1.2s
 => exporting to image                                                                                                                   1.5s
 => => exporting layers                                                                                                                  1.5s
 => => writing image sha256:281db5f2b3013ca9716a25802c1d12537b6e2479ab897719a35a15d048fcdead                                             0.0s
 => => naming to docker.io/library/logger                                                                                                0.0s
user@Syrex:~/Syrex333/workspace/lab08$ ocker images

Command 'ocker' not found, did you mean:

  command 'docker' from snap docker (27.5.1)
  command 'docker' from deb docker.io (26.1.3-0ubuntu1~20.04.1)

See 'snap info <snapname>' for additional versions.

user@Syrex:~/Syrex333/workspace/lab08$ docker images
permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Head "http://%2Fvar%2Frun%2Fdocker.sock/_ping": dial unix /var/run/docker.sock: connect: permission denied
user@Syrex:~/Syrex333/workspace/lab08$ sudo docker images
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
logger       latest    281db5f2b301   27 seconds ago   560MB
<none>       <none>    ff5c7678b138   12 minutes ago   572MB
user@Syrex:~/Syrex333/workspace/lab08$ sudo docker run -it -v "$(pwd)/logs/:/home/logs/" logger
root@2f8cc3466c58:/print# text1
bash: text1: command not found
root@2f8cc3466c58:/print# text
bash: text: command not found
root@2f8cc3466c58:/print# text 1
bash: text: command not found
root@2f8cc3466c58:/print# test1
bash: test1: command not found
root@2f8cc3466c58:/print# text1
bash: text1: command not found
root@2f8cc3466c58:/print# text2
bash: text2: command not found
root@2f8cc3466c58:/print# text3
bash: text3: command not found
root@2f8cc3466c58:/print# <C-D>
bash: syntax error near unexpected token `newline'
root@2f8cc3466c58:/print# ^C
root@2f8cc3466c58:/print# ^C
root@2f8cc3466c58:/print# E
bash: E: command not found
root@2f8cc3466c58:/print# <x-d>
bash: syntax error near unexpected token `newline'
root@2f8cc3466c58:/print# EXIT
bash: EXIT: command not found
root@2f8cc3466c58:/print# exit
exit
user@Syrex:~/Syrex333/workspace/lab08$ sudo  docker inspect logger
[
    {
        "Id": "sha256:281db5f2b3013ca9716a25802c1d12537b6e2479ab897719a35a15d048fcdead",
        "RepoTags": [
            "logger:latest"
        ],
        "RepoDigests": [],
        "Parent": "",
        "Comment": "buildkit.dockerfile.v0",
        "Created": "2025-05-11T18:46:44.575348619+03:00",
        "DockerVersion": "",
        "Author": "",
        "Config": {
            "Hostname": "",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "DEBIAN_FRONTEND=noninteractive",
                "TZ=Etc/UTC"
            ],
            "Cmd": [
                "/bin/bash"
            ],
            "Image": "",
            "Volumes": null,
            "WorkingDir": "/print",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {
                "org.opencontainers.image.ref.name": "ubuntu",
                "org.opencontainers.image.version": "20.04"
            }
        },
        "Architecture": "amd64",
        "Os": "linux",
        "Size": 560274098,
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/snap/docker/common/var-lib-docker/overlay2/46bg3e0ihsd7jnipwdlyxpw1v/diff:/var/snap/docker/common/var-lib-docker/overlay2/yl45xwgqgc9tf8cdx60jnitpu/diff:/var/snap/docker/common/var-lib-docker/overlay2/ncvxhspl6d4ogep5hss5xdscn/diff:/var/snap/docker/common/var-lib-docker/overlay2/kcyzz9zdtakrq548j29nwbqym/diff:/var/snap/docker/common/var-lib-docker/overlay2/lkmvkegale4ensa6o5ffx9kqd/diff:/var/snap/docker/common/var-lib-docker/overlay2/t7nq294ogbswo7ykj1luqhnq3/diff:/var/snap/docker/common/var-lib-docker/overlay2/bb540c76bf2a79b27f27e139c8febb4e87719983a8d07185a59a1ffc254c972f/diff",
                "MergedDir": "/var/snap/docker/common/var-lib-docker/overlay2/kz40p9kv8vd7pdkozahhr8tb8/merged",
                "UpperDir": "/var/snap/docker/common/var-lib-docker/overlay2/kz40p9kv8vd7pdkozahhr8tb8/diff",
                "WorkDir": "/var/snap/docker/common/var-lib-docker/overlay2/kz40p9kv8vd7pdkozahhr8tb8/work"
            },
            "Name": "overlay2"
        },
        "RootFS": {
            "Type": "layers",
            "Layers": [
                "sha256:470b66ea5123c93b0d5606e4213bf9e47d3d426b640d32472e4ac213186c4bb6",
                "sha256:9fdb75cc687d01660a790df48f7ec96dc6a69b034bff49ba99854f83d9eca25c",
                "sha256:3f92a326969879a63e07111a5901297811968b6e0c20df7940d62bc28b2a6967",
                "sha256:5f70bf18a086007016e948b04aed3b82103a36bea41755b6cddfaf10ace3c6ef",
                "sha256:2c58d6f43c54c5e46a2da36c8e49f0093701405c1a60d28dbef45de8cc571a83",
                "sha256:5f70bf18a086007016e948b04aed3b82103a36bea41755b6cddfaf10ace3c6ef",
                "sha256:01b8edc69a806e29fd85a8caebdf2fee4e0667a56b56ec6788b7e542245c4dd5",
                "sha256:1d5af48f937eb587794f56b02069e57d91a05f09f6fd6b0ed3588841a7b99f2e"
            ]
        },
        "Metadata": {
            "LastTagTime": "2025-05-11T18:46:46.114992541+03:00"
        }
    }
]
user@Syrex:~/Syrex333/workspace/lab08$  cat logs/log.txt
cat: logs/log.txt: No such file or directory
user@Syrex:~/Syrex333/workspace/lab08$ mkdir logs
mkdir: cannot create directory ‘logs’: File exists
user@Syrex:~/Syrex333/workspace/lab08$ cd logs
user@Syrex:~/Syrex333/workspace/lab08/logs$ ls
user@Syrex:~/Syrex333/workspace/lab08/logs$ touch log.txt
user@Syrex:~/Syrex333/workspace/lab08/logs$ ls
log.txt
user@Syrex:~/Syrex333/workspace/lab08/logs$ cd ..
user@Syrex:~/Syrex333/workspace/lab08$  cat logs/log.txt
user@Syrex:~/Syrex333/workspace/lab08$  gsed -i 's/lab07/lab08/g' README.md

Command 'gsed' not found, did you mean:

  command 'msed' from deb mblaze (0.6-1)
  command 'gsad' from deb greenbone-security-assistant (7.0.3+dfsg.1-1)
  command 'gsnd' from deb ghostscript (9.50~dfsg-5ubuntu4.15)
  command 'gsec' from deb firebird3.0-utils (3.0.5.33220.ds4-1build2)
  command 'ssed' from deb ssed (3.62-7build1)
  command 'sed' from deb sed (4.7-1)

Try: sudo apt install <deb name>

user@Syrex:~/Syrex333/workspace/lab08$ sudo  gsed -i 's/lab07/lab08/g' README.md
sudo: gsed: command not found
user@Syrex:~/Syrex333/workspace/lab08$  sed -i 's/lab07/lab08/g' README.md
user@Syrex:~/Syrex333/workspace/lab08$ git add Dockerfile
user@Syrex:~/Syrex333/workspace/lab08$ git add .travis.yml
user@Syrex:~/Syrex333/workspace/lab08$ git commit -m"adding Dockerfile"
[main 4ce9a3d] adding Dockerfile
 1 file changed, 31 insertions(+)
 create mode 100644 Dockerfile
user@Syrex:~/Syrex333/workspace/lab08$ git push origin main
Username for 'https://github.com': Syrex333
Password for 'https://Syrex333@github.com':
To https://github.com/Syrex333/lab08
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/Syrex333/lab08'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
user@Syrex:~/Syrex333/workspace/lab08$ git pull origin main
warning: no common commits
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), 855 bytes | 855.00 KiB/s, done.
From https://github.com/Syrex333/lab08
 * branch            main       -> FETCH_HEAD
 * [new branch]      main       -> origin/main
fatal: refusing to merge unrelated histories
user@Syrex:~/Syrex333/workspace/lab08$ git push origin main
Username for 'https://github.com': Syrex333
Password for 'https://Syrex333@github.com':
To https://github.com/Syrex333/lab08
 ! [rejected]        main -> main (non-fast-forward)
error: failed to push some refs to 'https://github.com/Syrex333/lab08'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
user@Syrex:~/Syrex333/workspace/lab08$ git add .
user@Syrex:~/Syrex333/workspace/lab08$ git commit
Aborting commit due to empty commit message.
user@Syrex:~/Syrex333/workspace/lab08$ git push --force origin main
Username for 'https://github.com': Syrex333
Password for 'https://Syrex333@github.com':
Enumerating objects: 258, done.
Counting objects: 100% (258/258), done.
Delta compression using up to 16 threads
Compressing objects: 100% (123/123), done.
Writing objects: 100% (258/258), 957.51 KiB | 119.69 MiB/s, done.
Total 258 (delta 102), reused 254 (delta 101)
remote: Resolving deltas: 100% (102/102), done.
remote: error: GH013: Repository rule violations found for refs/heads/main.
remote:
remote: - GITHUB PUSH PROTECTION
remote:   —————————————————————————————————————————
remote:     Resolve the following violations before pushing again
remote:
remote:     - Push cannot contain secrets
remote:
remote:
remote:      (?) Learn how to resolve a blocked push
remote:      https://docs.github.com/code-security/secret-scanning/working-with-secret-scanning-and-push-protection/working-with-push-protection-from-the-command-line#resolving-a-blocked-push
remote:
remote:
remote:       —— GitHub Personal Access Token ——————————————————————
remote:        locations:
remote:          - commit: 4289b3460b8d328b76d4a9b156c9b636968b2a2c
remote:            path: the order of execution of commands:2
remote:          - commit: 6d1bedf67d6bdb83b18bd2337f8f0f953e416ff2
remote:            path: the order of execution of commands:2
remote:
remote:        (?) To push, remove secret from commit(s) or follow this URL to allow the secret.
remote:        https://github.com/Syrex333/lab08/security/secret-scanning/unblock-secret/2wxMzqUxXQOaePLH5vZWePejZ9f
remote:
remote:
remote:
To https://github.com/Syrex333/lab08
 ! [remote rejected] main -> main (push declined due to repository rule violations)
error: failed to push some refs to 'https://github.com/Syrex333/lab08'
user@Syrex:~/Syrex333/workspace/lab08$  git push --force origin main
Username for 'https://github.com': Syrex333
Password for 'https://Syrex333@github.com':
Enumerating objects: 258, done.
Counting objects: 100% (258/258), done.
Delta compression using up to 16 threads
Compressing objects: 100% (123/123), done.
Writing objects: 100% (258/258), 957.51 KiB | 106.39 MiB/s, done.
Total 258 (delta 102), reused 254 (delta 101)
remote: Resolving deltas: 100% (102/102), done.
To https://github.com/Syrex333/lab08
 + d0d2aef...4ce9a3d main -> main (forced update)
