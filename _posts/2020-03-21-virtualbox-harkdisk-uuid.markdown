---
title: Change VirtualBox harddisk uuid
layout: post
date: '2020-03-21 13:59:00 +0700'
categories: virtualbox
---

I found one of my old VMs can not be imported into VirtualBox. The tool showed me this following error message:

Cannot register the hard disk XXX because a hard disk YYY with UUID ZZZ already exists.

Normally, we do not meet this issue when using VirtualBox to clone VMs. But sometimes, we did copy .VDI files insead of cloning the VMs. It is a quicker method but the drawback is the harddisk's uuid conflict. 

Fortunately, VirtualBox has an internal and undocumented command called sethduuid. 
{% highlight shell %}
VBoxManage.exe internalcommands sethduuid <path to the .vdi/.vmdk disk image>
{% endhighlight %}
VirtualBox then will create a new uuid and assign it to the .vdi file.

Mac Os or Linux users use VBoxManage instead of VBoxManage.exe like this:
{% highlight shell %}
VBoxManage internalcommands sethduuid <path to the .vdi/.vmdk disk image>
{% endhighlight %}

To verify the uuid of your .vdi hardisk image, use this command:

{% highlight shell %}
VBoxManage.exe showhdinfo <path to the .vdi/.vmdk disk image>
{% endhighlight %}

NOTE: The above commands can be used with snapshots disk image too:
{% highlight shell %}
VBoxManage internalcommands sethduuid ./Snapshots/file.vdi
VBoxManage showhdinfo ./Snapshots/file.vdi
{% endhighlight %}

Lastly, updating the uuid is not enough. We should also change the .box file

 - back up the .vbox file before opening it in a text editor
 
 - replace the UUID found in <HardDisk uuid="{...}" and in <Image uuid="{}" (towards the end) with the UUID you got when you ran sethduuid

NOTE:

If VirtualBox reported the error messsage: 

Trying to open a VM config [...] which has the same UUID as an existing virtual machine

We will need to update the UUID of the machine in the .vbox file too:

 - run VBoxManage internalcommands sethduuid <VDI/VMDK file> twice instead one !

 - back up the .vbox file before opening it the .vbox file in a text editor
 
 - replace the UUID found in <HardDisk uuid="{...}" and in <Image uuid="{}" (towards the end) with the UUID you got when you ran sethduuid

 - replace the UUID found in <Machine uuid="{...}" with the UUID you got when you ran sethduuid

 NOTE:
 - If you made mistake when updating uuid, you can rollback the .vbox file
 - To rollback the .vdi/.vmdk file, you can run sethduuid with the last parameter is the previous uuid:

{% highlight shell %}
VBoxManage.exe internalcommands sethduuid <path to the .vdi/.vmdk disk image>  <previous uuid>
{% endhighlight %}