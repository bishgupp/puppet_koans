Ordering
--------

A student one day decides to test the efficiency and accuracy of the 
Puppet Master. He configures a puppet agent on a node and asks for a catalog.

He receives the catalog. "A B C"
He then again asks the PuppetMaster for the catalog. He receives the catalog "B A C".

He looks up at the catalog smiling and then again asks for the catalog.
The Master gives him this time "C A B".

Smiling happily at having caught the PuppetMaster's mistake and finally getting 
a chance at showing off, he decides to point out the mistake to the Master.

He says "Master, I asked you for a catalog 3 times. And each of the time, you 
gave me the Resources in catalog in different order! This is absolute chaos!"

The Master smiled and pointed at the pebbles in the garden and said.

"There is always Harmony in Chaos."

[1]

Resources, resources and resources.
-----------------------------------

A curious newbie student asks the PuppetMaster.

"What do you do with the Puppet nodes ?"

"I give them Resources.", the master replies, smiling.

[2]

Being
-----

A student asked the PuppetMaster,
"What does a machine do when it has Puppet agent ?"

The PuppetMaster replied,
"It does not do, it is."

[3]


Requiring
---------

A student, puzzled with a mysterious error that he was getting, came frustrated
to the Puppetmaster. He was quite sure that this time he had found some weird bug
in teachings.

Trying to keep his calm, the student asked,
"Master, why do I get this weird error -- Duplicate declaration: Class A is already declared; cannot redeclare on node X ?"

"Because Class A is already included.", the master replied calmly.

"But, I haven't! It is only included once in the site manifest for the node X", the student replied, almost losing his temper.

The PuppetMaster smiled.

The student finally lost his temper. 
"In fact, even if I do not `include` the class in the site manifest, Puppet processes it! How can it be ? This is absurd!"

"Do you require Class A ?", the PuppetMaster asked, calmly again.

The student was puzzled.

"Yes, of course. I want it to be included!"

"Do you `require` Class A ?", the master asked again, this time indicating he was using a word from the Language of Puppet.

"Yes, I have `require`d it"
Racking his brains, the student replied.

And the PuppetMaster said,
"If you `require` it, it will be also `include`-d. "

The student thought about it for some time. 

"Then, what should I do ? How can I require the class but not include it ?"

"Chain it using arrows.", the PuppetMaster replied.

[4]


# # #

[1]: Commentary on the 'Ordering' koan

It should not matter what order resources in a catalog are executed, they should
still work the same way. Thus if you are depending too much on Ordering your 
resources, you should re-think of how are your modules and  resources organized.
Because Puppet, actually, always sends the resources in the catalog in a random 
order, unless an order is explicitly provided, everytime any node issues a 
catalog request and this can be tedious easily with many nodes, even if you use 
stages.

[2]: Commentary on the 'Resources, resources and resources' koan

Puppet essentially deals with Resources -- a bit like SoA where we talk only in
terms of Services, and everything makes up only a service, in Puppet, we talk 
only in terms of Resources and everything essentially, in the end, makes up a 
Resource. Even if you are using something like 'Exec', it should ultimately 
lead to providing a Resource to the node and not a one-off command that is to 
be executed on the machine.

Read the last para of the beginning notes at [Puppet Reference for exec](http://docs.puppetlabs.com/references/latest/type.html#exec)

[3]: Commentary on the 'Being' koan:

Puppet agent, essentially, tells how a machine should be (like it should have X
package installed, Y service running and Z file at PQR location) and NOT what 
the machine should do (it should install XYZ package OR it should run some Z 
command)

[4]: Commentary on the 'Requiring' Koan:

If you 'require' a class inside another class, it does two things:
1. Creates a dependency for that class ie. the target class will be processed before the current class.
2. Declares that class.

This is because `require` function has `include`-like behaviour. Read more [here](http://docs.puppetlabs.com/puppet/3/reference/lang_classes.html#include-like-behavior)

Thus, if you want to merely say that a class X depends on class Y, you can use 
relationship chaining arrows to state the dependency inside Class X or Class Y.

To do this, put `Class ['X'] -> Class ['Y']` inside either class X or class Y.

