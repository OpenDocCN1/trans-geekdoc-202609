It's not hard to move around between checkpoints. However, if you want to preserve the current state, you need to take a new checkpoint. If you don't, the latest preserved state is that of its latest checkpoint. So, to go to a different checkpoint while the one is running, you do the following:

+   - Select the checkpoint you want to move to.

You can select any one you like, even the ones in the middle of a chain.

+   - Use the Apply from the Checkpoint menu.

You get a dialog box with three choices: Create Checkpoint and Apply (the default), Apply, and Cancel.

+   - Make your choice, and after a couple of seconds, the selected checkpoint starts running.

In the same way, you can delete any checkpoint you want. From the management console, this seems simple, but under the hood there is more going on. The key is using differing checkpoints. What happens if you remove a checkpoint in the middle of a chain? In that case, the differencing files of the removed checkpoint are preserved, keeping the disk intact. In Hyper-V 2012, you can merge the orphaned disks into yours without downtime. The Hyper-V management console will show a status of Mer (and will indicate the percentage completed). There are more scenarios to consider here, but the key point is that Hyper-V is aware of them and will do the right thing.

One example is when you remove the virtual disks. The dialog box will tell you that it will not remove the virtual disks. That's only partially true. When you delete the VM, it will take longer than you might expect. A dialog box onscreen telling you that it is Destroying (and will indicate a percentage) and counting. It is not removing the disks; it is merging the checkpoint with its parents, leaving you with just one .vhdx file representing the data of the VM you just deleted. That's probably the right thing to do, anyway

As a testing feature, checkpoints are great. You can mess up any environment you want and have your get-out-of-free card to bail out. No? always. There are situations where applying an earlier checkpoint can get you into trouble. For a stand-alone configuration without relations to others, checkpoints are perfectly safe. For any situation where computers share some configuration, you need to be careful. The best example of this is Active Directory.

In fact, there are a of ways that checkpoints can get you into trouble with Active Directory. The most obvious example is when you have a member server latest 40 days ago. So you know, that a server that is member of a domain changes its password every 30 days. Since 40 days ago, that server has changed its password in Active Directory at least once and twice. In its local database, it stores two passwords, the current and the previous. If it has changed its password twice, the checkpointed server has no matching password in Active Directory. In other words, it is no longer a member of the domain and needs to be rejoineded. This problem is the same as with regular backups. However, there is a more subtle and dangerous problem that affects any regular controller with a version of Active Directory earlier than Windows Server 2012 (RTM).