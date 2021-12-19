# Automatic-Theme-Changer
Are you tired of changing themes every evening and morning. Well this might come in handy to such people, use these commands to automate the theme changing part at your definite intervals.
-----
Alongside the slew of personalization settings, Windows 10 ships with two color modes, including the "light" color mode, which applies a lighter color scheme across apps and desktop elements, such as Start menu, taskbar, and action center, and it's a mode that works well during daytime. Then there's the "dark" color mode that allows you to set a darker set of colors across the desktop and apps, and it's more suited for low-light environments.
Whether you like the lighter or darker colors on your device, Windows 10 makes it easy to change modes using the Settings app. However, it doesn't offer an option to switch between the two color modes depending on the time of day automatically, similar to other OSes, including Xbox One.

If switching between dark and light (and vice versa) is an option you would like to have on your device, you can create an automated process using the Task Scheduler and a few simple PowerShell commands to modify the Registry to switch to light mode during the day and dark mode at night, automatically.
We walk you through the steps to configure your device to switch between the light and dark system modes depending on the time of day, using a few PowerShell commands and Task Scheduler.

AUTOMATIC SETUP

###################

1.Open Task Scheduler and import these two files in my repo 
2.Click OK 

That's it !

MANUAL SETUP

###################.

1.Open Start.

2.Search for Task Scheduler and click the top result to open the app.

3.Expand the Task Scheduler Library folder.

4.Right-click the "Task Scheduler Library," and select the New Folder option.

5.Type a name for the folder (for example, MyTasks), and click the OK button.

(Quick note: We're creating a new folder to keep your tasks and system tasks separate, which makes it easier to manage tasks.)

6.Right-click the "MyTasks" folder (if applicable), and select the Create Task option.

7.Click on the "General" tab.

8.Under the "Name" field, enter a descriptive name for the task. (For example, light_mode).

9.Under the "Security options" section, select the option Run only when the user is logged in.

10.Click on the Triggers tab.

11.Click the New button.

12.Under "Begin the task," select the On a schedule option. (You can configure any trigger you want.)

13.Under the "Settings" section, select the Daily option.

14.Set the time you want Windows 10 to switch automatically to the light mode. (For example, 6:30 a.m.)

15.Click the OK button.

16.Click on the Actions tab.

17.Click the New button.

18.Using the "Start a program" action, under the "Settings" section, copy and paste the following path:

%SystemRoot%\system32\WindowsPowerShell\v1.0\powershell.exe

19.Under the "Add arguments (optional)" field, copy and paste the following PowerShell command:

New-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Themes\Personalize -Name SystemUsesLightTheme -Value 1 -Type Dword -Force; New-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Themes\Personalize -Name AppsUseLightTheme -Value 1 -Type Dword -Force

(The above command will try to create a SystemUsesLightTheme and AppsUseLightTheme DWORD in the Registry and set their values to 1, which disables the dark and enables the light color mode across apps and desktop.)

20.Click the OK button.

21.Click on the Settings tab.

22.Check the Run task as soon as possible after a scheduled start is missed option, which should help to run the command if Task Scheduler misses the schedule because your computer was asleep.

23.Check the If the task fails, restart every option, and make sure it's set to 1 minute and only 3 restart attempts.

24.Click the OK button.

25.Once you complete these steps, every day at the time you specified Windows 10 will switch to the light mode for apps and the desktop environment automatically.

26.Right-click the "MyTasks" folder (if applicable), and select the Create Task option.

27.Click on the "General" tab.

28.Under the "Name" field, enter a descriptive name for the task. (For example, dark_mode).

29.Under the "Security options" section, select the option Run only when the user is logged in.

30.Click on the Triggers tab.

31.Click the New button.

32.Under "Begin the task," select the On a schedule option. (You can configure any trigger you want.)

33.Under the "Settings" section, select the Daily option.

34.Set the time you want Windows 10 to switch automatically to the dark mode. (For example, 6:30 p.m.)

35.Click the OK button.

36.Click on the Actions tab.

37.Click the New button.

38.Using the "Start a program" action, under the "Settings" section, copy and paste the following path:

%SystemRoot%\system32\WindowsPowerShell\v1.0\powershell.exe

39.Under the "Add arguments (optional)" field, copy and paste the following PowerShell command:

New-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Themes\Personalize -Name SystemUsesLightTheme -Value 0 -Type Dword -Force; New-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion\Themes\Personalize -Name AppsUseLightTheme -Value 0 -Type Dword -Force

(The above command will try to create a SystemUsesLightTheme and AppsUseLightTheme DWORD in the Registry and set their values to 1, which disables the dark and enables the light color mode across apps and desktop.)

40.Click the OK button.

41.Click on the Settings tab.

42.Check the Run task as soon as possible after a scheduled start is missed option, which should help to run the command if Task Scheduler misses the schedule because your 
computer was asleep.

43.Check the If the task fails, restart every option, and make sure it's set to 1 minute and only 3 restart attempts.

44.Click the OK button.

##########################

After you completing the steps, every day at the time you specified Windows 10 will switch to the dark mode for apps and the desktop environment automatically.

If you want to make sure the task is working, you can always right-click the tasks, and select the Run option.

When you no longer need this feature, you can open the Task Scheduler folder with the tasks you created, and then right-click and delete each task. Then you can continue to use the Settings app to switch modes from the "Personalization" page.
