
o3de_gem_setup("BasePlanet")

# This indicates to the Builders applications(AssetProcessor, AssetBuilder, AssetBundler)
# that the gem should be added to the "cmake_dependencies.<project>.assetbuilder.setreg"
# which is generated when cmake configure occurs.
# Also tooling applications such as the Editor needs the CMake alias
# to see the gem as active
if(PAL_TRAIT_BUILD_HOST_TOOLS)
    ly_create_alias(NAME ${gem_name}.Builders NAMESPACE Gem)
    ly_create_alias(NAME ${gem_name}.Tools NAMESPACE Gem)

    # Add in CMake dependencies for each gem dependency listed in this gem's gem.json file
    # for the Tools and Builders gem variants
    o3de_add_variant_dependencies_for_gem_dependencies(GEM_NAME ${gem_name} VARIANTS Tools Builders)
endif()
