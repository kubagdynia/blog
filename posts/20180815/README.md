![](D:\Dev\blog\posts\20180815\img\lazarustinyradioplayer.jpg)

# Tiny Radio Player #01 – Introduction

In the first and several following posts, I would like to reach back into the past and check if it is still possible to successfully write applications in Pascal today. However, I'm not talking about Delphi or Turbo Pascal, but about the free Free Pascal integrated with the [Lazarus](https://www.lazarus-ide.org/) development environment. With its help, we will write, or at least try to write, an application for playing online radio stations. Lazarus is a cross-platform environment, so we assume from the start that we are writing for Windows, Linux, and Mac OSX systems. This is one of the main advantages of Lazarus. An application written for Windows can then be compiled and run on Linux or Mac OSX without any modifications.

Well, but let's consider what exactly we will need to write such a radio player. We already have the development environment. The code will be placed on [GitHub](https://github.com/kubagdynia/TinyRadioPlayer). Therefore, we still need some audio library. I suggest using [BASS](https://www.un4seen.com/). It is a free library with support for all the systems we are interested in. Additionally, it allows downloading basic information about the radio being played, recording sound to a file, and using filters such as echo or compressor. The only thing missing for complete happiness is a database. I chose [SQLite](https://www.un4seen.com/) because it is fast and stored in a single file.

## Installation

To install Lazarus on Windows, go to the downloads page and download the 32-bit version of the installer. For Linux and Mac OSX, follow a similar procedure, downloading the installer for the appropriate system.

## Adding a New Project, Initial Configuration, and Changing the IDE Language

After launching Lazarus, I suggest changing the IDE language to English since all the descriptions will be based on this version. To do this, click on **Tools -> Options**, select **Environment -> General**, and change the Language to **English [en]**. After clicking the **[OK]** button, close and restart Lazarus.

To create a new project, click **File -> New...** and choose **Project -> Application**.

![](D:\Dev\blog\posts\20180815\img\001LazarusNewProject.jpg)

Next, change the name of the main form from **Form1** to **MainForm** (Name parameter).

![](D:\Dev\blog\posts\20180815\img\002LazarusChangeNameOfMainForm.jpg)

We also change the caption of the main form to Tiny Radio Player (**Caption** parameter), which will be displayed as the application's description. Additionally, we change the position of the main window to **poScreenCenter** (**Position** parameter). After this change, if we run the application, it will be displayed in the center of the screen.

Finally, we change the application's name to Tiny Radio Player. We can do this by going to the project options **Project -> Project Options...** and changing the **Title** parameter. From the project options screen, we can also change the application's icon. For now, let's leave it as default.

## Configuration and First Launch

To make it easier to manage the project, we will change the configuration of the directories where files will be saved during compilation.

Go to the project options **Project -> Project Options...** and navigate to the compilation options **Compiler Options**. Then, change the settings in the following way:

**Other unit files (-Fu):** *../lib/$(TargetCPU)-$(TargetOS)*
**Unit output directory (-FU):** *../compiled/$(TargetCPU)-$(TargetOS)*
**Target file name (-o):** *../bin/$(TargetCPU)-$(TargetOS)/TinyRadioPlayer*

![](D:\Dev\blog\posts\20180815\img\003LazarusCompilerOptionsPaths.jpg)

If clicking **[OK]** displays a message about a missing directory, click **Ignore**.

Now it's time to save the project. We click **File -> Save All**. Then we create a directory named **TinyRadioPlayer** and inside it a directory named **source**. We change the file name to **TinyRadioPlayer.lpi**. We click **Save** and proceed to the next step, where we change the name of the main form file from **unit1.pas** to **MainFormUnit.pas** and click **Save** again.