Paste these files in app/libs

And add these lines in app build.gradle

dependencies {
    compileOnly(files("libs/api-82.jar"))
    compileOnly(files("libs/api-82-sources.jar"))
}
