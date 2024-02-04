cmake_minimum_required(VERSION 2.7)

project(ecdsa++)

include(FetchContent)
FetchContent_Declare(
    secp256k1
    GIT_REPOSITORY https://github.com/bitcoin-core/secp256k1.git
)
FetchContent_MakeAvailable(secp256k1) #获取sep256k1库


find_package(OpenSSL REQUIRED)
find_library(PTHREAD pthread)


file(GLOB src "./src/*")
add_library(ecdsa++ SHARED ${src})
target_link_libraries(ecdsa++ secp256k1 ${OPENSSL_LIBRARIES} ${PTHREAD})

