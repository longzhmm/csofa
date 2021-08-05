# csofa built into an vcpkg CMake port.

# =====================================
# portfile.cmake 
# csofa的cmake的编译信息
# =====================================
# portfile.cmake
vcpkg_from_github(
    OUT_SOURCE_PATH SOURCE_PATH
    REPO longzhmm/csofa
    REF 9092d7deed92bc736a8493dc2927d3949ece7577
    SHA512 2ed3966eb2e8e4413300f3c09ac1a2124e708313b0f1360f64e57fe5de6f7b67c78702c91606161cfae24ca2516dac0665c0f85251328b89e70fafa3f2d70a31
    HEAD_REF main
)

vcpkg_configure_cmake(
    SOURCE_PATH ${SOURCE_PATH}
    PREFER_NINJA
    OPTIONS 
        -DBUILD_csofa_TESTS=OFF   
)

vcpkg_install_cmake() 
 
vcpkg_fixup_cmake_targets(CONFIG_PATH lib/cmake/csofa)

vcpkg_copy_pdbs()

file(REMOVE_RECURSE "${CURRENT_PACKAGES_DIR}/debug/include")

file(INSTALL ${SOURCE_PATH}/LICENSE DESTINATION ${CURRENT_PACKAGES_DIR}/share/${PORT} RENAME copyright)

file(INSTALL ${SOURCE_PATH}/LICENSE DESTINATION ${CURRENT_PACKAGES_DIR}/share/${PORT} RENAME copyright)
# --------------------------------------------



# =====================================
# vcpkg.json文件，包含名称、版本、以及所需依赖vcpkg库
# =====================================
# vcpkg.json
{
	"name": "csofa",
	"version-string":"1.0",
	"description":"csofa are from SOFA Software"
}
# --------------------------------------------



# =====================================
# vcpkg-configuration.json文件
# 全部安装完成后集合到vs中会用到registries文件，
# 文件内为vcpkg库的下载源
# =====================================
# vcpkg-configuration.json
{
    "registries": [
        {
            "kind": "git",
            "repository": "https://github.com/longzhmm/csofa.git",
            "packages": [ "csofa" ]
        }
    ]
}

# --------------------------------------------

