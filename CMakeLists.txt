cmake_minimum_required(VERSION 3.15)
project(discord-bot VERSION 1.0 DESCRIPTION "A discord bot")
enable_testing()

#find_package(ZLIB REQUIRED)
#find_package(OpenSSL REQUIRED)
find_package(OpenSSL REQUIRED)
find_package(ZLIB REQUIRED)

# Linking libraries

# target_link_libraries(dpp
#     OpenSSL::OpenSSL
#     ZLIB::ZLIB
# )

add_subdirectory(libs/DPP)

# Create an executable
add_executable(${PROJECT_NAME}
    src/main.cpp
    # your other files...
)

target_link_libraries(${PROJECT_NAME} PUBLIC
    OpenSSL::SSL
    OpenSSL::Crypto
    openssl::openssl
    ZLIB::ZLIB
    dpp
    # Add any other libs you want to use here
)

target_compile_features(dpp PUBLIC cxx_std_20)