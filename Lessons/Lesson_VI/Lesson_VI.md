-- *Slide* --

## Lesson VI: Snapshots, backups and vertical scaling (30 min)

http://tinyurl.com/rc-issue-14

-- *Slide End* --

## Snapshots

> Having updated her site, and made an off site backup of the data, Anna realises that if anything happened to the 
> machine that her site was on, she would have to go to a lot of effort to restore the site. She mentions this to
> a more technically literate friend, Sandy, saying "If only I could make a copy of it! Something like a photograph
> \- quick and easy to do!".  Sandy laughs, and says: "Odd you should say 'photograph', as NeCTAR give you a facility to
> make a copy of a running machine. The term they use is 'snapshot'. The button to take it is right up there on the
> list of running instances in the dashboard. Give it a try next time you are logged in!"

-- *Slide* --

## Exercise 1

Can you make a snapshot of your running VM?

Find the snapshot button next to your running instance of Drupal, and make a snapshot of it. Give it a useful name
that will allow you to know what it is when you come back to it weeks later.

-- *Slide End* --

---

Hold up a Green card once the creation of the snapshot of your instance has started.
And a Red card if you need help.

---

Whilst your snapshots are being taken, lets talk about what has just gone on under the hood.

The running virtual machine is suspended on its host machine for a short while. Whilst it is suspended a copy is made
of the underlying disk. Remember that in this virtual environment disks are just files on the host server. So making
a copy is just like making a copy of a large file on your desktop.

Once the copy is complete the virtual machine is restarted. Then finally the copy of the disk is 
transferred to the Research Cloud image store.

When this process is completed your snapshot will appear on the images tab of your project, with a type of "Snapshot". 
If all has gone well, the dashboard will take you to this tab automatically.

-- *Slide* --

## Exercise 2

In home directory, run the script `loop.sh` by:

``` bash
./loop.sh
```

Watch the output as you make a snapshot of your instance!

When done kill the script by hitting the `Ctrl` and `C` keys together. 

-- *Slide End* --

---

This exercise gives you a feel for the duration of the suspension. The script will start to count up, at the rate of one
count every half second or so. Readjust the windows on your desktop so that you can see the output in the terminal 
window as you snapshot your running instance. Then make a snapshot, and watch what happens to the output of the 
loop script.

All going well, you should see the output pause for a few seconds, then resumes. On the other hand, the dashboard will 
continue well after the count has resumed... 

Remember, to stop `loop.sh` from running, simply press the 'Ctrl' and the 'c' key together.

Hold up a Green card once you have seen the output pause.
And a Red card if you need help.

---

-- *Slide* --

## Thought experiment

Why does the loop resume well before the dashboard shows the snapshot is complete?

-- *Slide End* --

A: the dashboard takes longer, as it has to write the copy of the disk to the image store.


So snapshots look like they might be the answer to Anna's problem, but they will have a short impact on anyone
who is using her site at the time they taken.

# Backups

> Anna is delighted to have a way of making a convenient backup of the site. But when she tells another friend, Ben,
> of her discovery he is very dismissive: "Oh, that's just broken" he says.

-- *Slide* --

## Question 1 

Why does Ben think snapshots are broken?

1. They are just too easy to do: suspicious enough!
1. The magic nostrums aren't up to the task!
1. Ben likes a life more complicated
1. The state of the machine is not captured
1. Cosmic rays can flip their bits.

-- *Slide End* --

---

**Answer 1**

    Whilst E is a topic for a good debate, the answer is:
    D. The state of the machine is not captured 

---

Let's take a look at this for a moment. The machine is paused, and then a copy of the hard drive is made. So any data
transfers that are happening between the machines drive and processor will be stopped mid flow. And then resumed
afterwards. So if its a file being read, all well and good. But what about files that are being written? Well, they 
might be caught mid write: which means that they won't be correctly captured.

**Q**  

Hold up a Red sticky note if you agree with Ben, 
and a Green one if you think that, snapshots are good to go.

**A** The reds have it. Sadly, Ben is right. Snapshots, although seductively easy to do, are prone to occasional 
failure due to writes not being captured. The interesting thing about this is that you might never notice that your 
data has been corrupted in this way.

-- *Slide* --

## Exercise 3

Delete your older, possibly unreliable, snapshot.

-- *Slide End* --

---

Hold up a Red sticky note if you need help,
Otherwise a green one when you are done.

---

> Alarmed by what Ben has told her, Anna does her research. And finds that in order to take good snapshots, she has
> to make sure that running programs have all written their contents to disk before the snapshot is made. There are
> a raft of fairly complicated steps that she has to take on the virtual machine to make sure that this is the case.
> Ann is depressed. But then she has an epiphany. If she shuts of her instance, then takes a snapshot of the shut
> off instance, all should be well.

-- *Slide* --

## Exercise 4

Power down your vm *by shutting it off!*

<span style="color:red">*Do not terminate it!*</span>
 
Then when it is in the shutoff state, make a snapshot of it.

-- *Slide End* --

---

Power down your instance by shutting it off, then make a snapshot of it. Remember to wait till your instance is in the
shut off state before you try to make your snapshot.

Hold up a Red sticky note if you need help,
Otherwise a green one when you are done.

---

-- *Slide* --

## Question 2 

What's a big problem with Anna's new approach?

1. You may forget to start your instance up again
1. The powered off machine might not have saved its state properly
1. The saved disk image is powerless
1. The process overhead is too high
1. How can you make a copy of a powered off disk?

-- *Slide End* --

---

**Answer 2**

A. You may forget to start your instance up again

---

Yes: not only are you taking your site offline for a longer period than the momentary pause of a regular snapshot,
you are opening yourself to the possibility of forgetting to start it up again when you are done.

Remember the checklists of lesson II? This is where the power of checklists can help you. 

If you have an important site
that you don't want to be down for extended periods create a checklist for this process.

Also, if you have a lot of users, notify them of the outage. It's only polite. Also consider doing it as a regularly
scheduled event.

-- *Slide* --

## Group Exercise 

Create a checklist for creating a snapshot of a running machine. 
Don't forget to notify your users!

-- *Slide End* --

## Restore

> Shortly after making her snapshot backup, Anna realizes that her instance is no longer responding to the outside
> world. After confirming that she didn't leave it in the shut down state, and with some trepidation, she shuts it down 
> and launches the snapshot backup.

This is where the rubber meets the road. 

-- *Slide* --

## Exercise 5

Terminate your running instance, then go to the images tab of your project
and launch a new instance using the snapshot that you have just created.
 
Once you are done make sure that your site is back up, and that you can ssh into the instance again.

Confirm that `today.txt` has your edits in it...

-- *Slide End* --

---

You can use the checklist from Lesson II as a memory jogger.

Hold up a Red sticky note if you need help,
Otherwise a green one when you are done.

---

## Vertical Scaling

> Anna's site is becoming increasingly popular, and some of her visitors are complaining that it's getting slow under
> the load.

-- *Slide* --

## Question 3

Anna's raft of kitten photographs has made it to the front page of the internet. Her server is struggling under the 
load. What can Anna do to solve this problem?

1. Nothing
1. Upgrade to a more powerful machine
1. Buy a physical machine and port her site to it
1. Make a support call to NeCTAR
1. Pay NeCTAR for more network

-- *Slide End* --

---

**Answer 3**

B. Upgrade to a more powerful machine

---

Remember the two nameless researchers whom I told you about at the start of these lessons, the two who spent over 
$20000 of their grant money on buying and upgrading their machines to complete their research? Well, if the 
Research Cloud had been around when they were doing their research, this is how simply they would have been able to 
resolve their problem.

-- *Slide* --

## Exercise 6

Terminate your running instance, and launch a new one 
using the snapshot that you have just created. 

But this time round, use the largest flavor
that your project will allow you.

-- *Slide End* --

---

Once you are done make sure that your site is back up, and that you can ssh into the instance again.

Again, you can use the checklist from Lesson II as a memory jogger.

Hold up a Red sticky note if you need help,
Otherwise a green one when you are done.

---

-- *Slide* --

## Question 4 

You'll notice that in your personal tenancy you can't run the largest machine image that you might want to.
What can you do to remedy this situation?

1. Nothing
1. Offer NeCTAR a load of money 
1. Reach for your credit card and call Amazon
1. Make a support call to NeCTAR
1. Go to the allocation tab and complete an allocation request

-- *Slide End* --

---

**Answer 4**

    E. Go to the allocation tab and complete an allocation request

---


-- *Slide* --

## Question 5

A volunteer please: to describe an image, an instance, and the difference between the two...

-- *Slide End* --