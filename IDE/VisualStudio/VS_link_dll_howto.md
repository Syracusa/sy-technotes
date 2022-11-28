
# dll Link
https://stackoverflow.com/questions/7845886/linking-dll-in-visual-studio

```
On Windows you do not link with a .dll file directly – you must use the accompanying .lib file instead. To do that go to Project -> Properties -> Configuration Properties -> Linker -> Additional Dependencies and add path to your .lib as a next line.

You also must make sure that the .dll file is either in the directory contained by the %PATH% environment variable or that its copy is in Output Directory (by default, this is Debug\Release under your project's folder).

If you don't have access to the .lib file, one alternative is to load the .dll manually during runtime using WINAPI functions such as LoadLibrary and GetProcAddress.
```