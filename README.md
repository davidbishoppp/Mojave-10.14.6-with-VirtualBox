# Mojave-10.14.6-with-VirtualBox

This guide is how I personaly set up my VM with Mojave and was able to update it to the latest vertion of 10.14.6.

## Step 1

Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads) and run the program. Then download the [Extension Pack](https://www.virtualbox.org/wiki/Downloads) for VirtualBox. This Extention will help solve the issue of not being able to control the mouse once the Vm is running.

## Step 2

* Open VirtualBox and click New.

* Click the Expert Mode button at the bottom of the new window.

* Name will be "MacOS". If you want to change the name to something else, you will have to edit the commands.bat file to match the new name.

* Type and Version should automaticly change. If not Type is Mac OS X and the Version is Mac OS X (64-bit).

* Set Memory Size to 2048MB or 4096MB, depends on how much you would like to use.

* Under hard disk section, select "Use and existing virtual hard disk file" and add the MacOS Mojave disk image

* Then click create.

## Step 3

* Open the settings for the new Vm.

* Go to System section.

* Under the Motherboad tab unselect Floppy.

* Under the Processor tab set the number of CPU cores to 2 or 4. (Half of your CPU core count).

* Go to Display section.

* Set video memory to 128MB.

* Go to Storage section.

* Delete the "Empty" optical drive.

* Create a new optical drive and add the APFS EFI Boot Image.

* Create a new hard disk and add the Update virtual disk.

* Go to USB section

* Select USB 3.0 (xHCI) Controller

## Step 4

VirtualBox must be closed for these next steps to work properly.

* Run the comands.bat file.

## Step 5

Once the VM boots to the shell run these comands:

``` code
edit startup.nsh
```

Then press enter.

In this next screen enter:

``` code
echo -off
load fs1:\EFI\drivers\apfs.efi
load fs1:\EFI\drivers\AppleUiSupport.efi
load fs1:\EFI\drivers\ApfsDriverLoader.efi
map -r
fs2:
cd System\Library\CoreServices\
boot.efi
```

To exit this screen press Ctrl-Q and then press Y.

Then type exit and enter.

And now press enter agin to continue