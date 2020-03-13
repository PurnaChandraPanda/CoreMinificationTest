# Minification for .NET Core app

This small adventure explains how to perform minification in Windows and Linux platforms.

## Windows
```
PS D:\work\samples\DotNetSample\MinificationTest\ConsoleApp1> dotnet publish -r win-x64 -c Release /p:PublishSingleFile=true /p:PublishTrimmed=true
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 146.71 ms for D:\work\samples\DotNetSample\MinificationTest\ConsoleApp1\ConsoleApp1.csproj.       ConsoleApp1 -> D:\work\samples\DotNetSample\MinificationTest\ConsoleApp1\bin\Release\netcoreapp3.1\win-x64\ConsoleApp1.dll
  Optimizing assemblies for size, which may change the behavior of the app. Be sure to test after publishing. See: https://aka.ms/dotnet-illink
  ConsoleApp1 -> D:\work\samples\DotNetSample\MinificationTest\ConsoleApp1\bin\Release\netcoreapp3.1\win-x64\publish\ 
```

-   Go to `bin\Release\netcoreapp3.1\win-x64\publish\` folder 
-   Run your app

```
PS D:\work\samples\DotNetSample\MinificationTest\ConsoleApp1\bin\Release\netcoreapp3.1\win-x64\publish> .\ConsoleApp1.exe
Hello World!
```

-   Now, you can just distribute the .exe for others to consume

## Linux

I have WSL ubuntu 18.04 installed. 

For Linux, can follow the same process with a slight change.

```
uadmin@MININT-BJ5SNCB:/mnt/d/work/samples/DotNetSample/MinificationTest/ConsoleApp1$ sudo dotnet publish -r linux-x64 -c Release /p:PublishSingleFile=true /p:PublishTrimmed=true
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 16.62 sec for /mnt/d/work/samples/DotNetSample/MinificationTest/ConsoleApp1/ConsoleApp1.csproj.
  ConsoleApp1 -> /mnt/d/work/samples/DotNetSample/MinificationTest/ConsoleApp1/bin/Release/netcoreapp3.1/linux-x64/ConsoleApp1.dll
  Optimizing assemblies for size, which may change the behavior of the app. Be sure to test after publishing. See: https://aka.ms/dotnet-illink
  ConsoleApp1 -> /mnt/d/work/samples/DotNetSample/MinificationTest/ConsoleApp1/bin/Release/netcoreapp3.1/linux-x64/publish/
```

Now, go to the node and execute it. Again, this can too be distributed in other Linux machines without .NET Core installed.

```
uadmin@MININT-BJ5SNCB:/mnt/d/work/samples/DotNetSample/MinificationTest/ConsoleApp1/bin/Release/netcoreapp3.1/linux-x64
$ ./ConsoleApp1
Hello World!
```

If it is a Windows machine, you can create runnable for Linux.

### Compile from Windows
```
PS D:\work\samples\DotNetSample\MinificationTest\ConsoleApp2> dotnet publish -r linux-x64 -c Release /p:PublishSingleFile=true /p:PublishTrimmed=true
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 162.12 ms for D:\work\samples\DotNetSample\MinificationTest\ConsoleApp2\ConsoleApp2.csproj.
  ConsoleApp2 -> D:\work\samples\DotNetSample\MinificationTest\ConsoleApp2\bin\Release\netcoreapp3.1\linux-x64\ConsoleApp2.dll
  Optimizing assemblies for size, which may change the behavior of the app. Be sure to test after publishing. See: https://aka.ms/dotnet-illink
  ConsoleApp2 -> D:\work\samples\DotNetSample\MinificationTest\ConsoleApp2\bin\Release\netcoreapp3.1\linux-x64\publish\
```

### Run from Linux
```
uadmin@MININT-BJ5SNCB:/mnt/d/work/samples/DotNetSample/MinificationTest/ConsoleApp2/bin/Release/netcoreapp3.1/linux-x64/publish
$ ./ConsoleApp2
Hello World!
```

## Reference
I scanned through a lot of documents for this purpose. However, in the time of need, [it](http://geekswithblogs.net/JeremyMorgan/archive/2019/07/24/creating-trimmed-self-contained-executables-in-.net-core.aspx) actually helped overcome my misconception.
