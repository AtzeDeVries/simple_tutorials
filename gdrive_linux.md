# How to use google drive on cli in linux

There is a nice tool called gdrive. This tool makes it easy to use google drive on commandline. It can be found over here
https://github.com/prasmussen/gdrive

### Example: Synchronize a linux folder with a google drive folder

First you need to install the tool in linux on your openstack instance. First log in into your instance. Then:
```
wget -O gdrive https://docs.google.com/uc?id=0B3X9GlR6EmbnQ0FtZmJJUXEyRTA&export=download
chmod +x gdrive
sudo mv ./gdrive /usr/bin/
```
The first time you use gdrive you need to authenicate.
```
gdrive list
```
Now it will display a link, copy this link to your webbrowser and it will return a code. Paste this code into you linux shell and the authenication should be fixed. Check it again with
```
gdrive list
```

Now in your webbrowser create a empty folder. Copy the last part of the URL. This is the ID of your folder. For example:
```
https://drive.google.com/drive/folders/0B0OqZDTfkBSmQzRtMnBkOGFYbEU
```
Here the ID is
```
0B0OqZDTfkBSmQzRtMnBkOGFYbEU
```
Now in your linux shell we create a directory and a test file.
```
mkdir test
cd test
echo 'bla' > bla.txt
```
Now let's sync this directory with google drive
```
gdrive sync upload ./ <ID>
```
Where `<ID>` is the id you just copied. It wil sync all files in this directory.

You can use `gdrive sync download` to download files from your drive folder to your linux instance.
