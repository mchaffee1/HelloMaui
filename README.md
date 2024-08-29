## HelloMaui
Running a couple experiments on the [.NET MAUI tutorial](https://dotnet.microsoft.com/en-us/learn/maui/first-app-tutorial/intro)

### Notes 
#### 2024-08-28
- Prepare VSCode
  - VSCode extension: .NET MAUI has 149k installs
    - compare 4.6MM for React Native Tools, 9MM for Flutter, 309k for Swift
  - Need to install .NET SDK 8 first (`brew install dotnet-sdk`)
  - Bunch of fiddling/restarting to convince VSCode to recognize Xcode
  - It keeps nagging about a Visual Studio subscription - but that doesn't seem strictly necessary so far?
- Hello World project
  - Generated from within VSCode, Cmd-shift-P -> ">.NET: New Project..." -> ".NET MAUI App"
  - Hot reload works - but seems only for layout, not code
  - The XAML format for views is... not beautiful
    - Individual component names are declared in XAML as string props, but then, magically, component references are treated like real objects by that name in CS files.
      - This *might* be fine but it feels janky
      - Cmd-click to chase a component reference throws an IDE error
      - Creating a new component in the .XAML and then having that name recognized as an object reference in the .XAML.CS file *does work* - if it didn't, I would consider that a dealbreaker
      - IDE/extension doesn't help with renaming components
  - Having separate files for layout and code might or might not be sustainable - need to play around more
  - Starter project is generated with Windows CRLFs
    - Had to run `git config core.autocrlf input` to make it behave
- Running the app on macOS
  - Simple app builds and launches in reasonable time
  - UI animation is happening by default without being requested (hopefully this is a configurable property on components?  Will research later)
- Running the app on iOS simulator
  - That was fine

### `//TODO` - further items to test
- Navigation
- UI customizations
- Investigate the [samples from dotnet](https://github.com/dotnet/maui-samples)
- Expensive features, e.g. camera, video player, etc
