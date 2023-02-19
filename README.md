### Building from the command line

With Xcode (succeeds):
```console
cmake -B build -G Xcode
xcodebuild -project build/ObjcSwiftNinja.xcodeproj -target ObjcSwiftNinja-app
```

With Ninja (fails):
```console
cmake -B build -G Ninja
ninja -C build ObjcSwiftNinja-app
```
