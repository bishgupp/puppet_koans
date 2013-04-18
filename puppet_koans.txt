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

The student asked the PuppetMaster,
"What does a machine do when it has Puppet agent ?"

The PuppetMaster replied,
"It does not do, it is."

[3]

# # #

[1]: Commentary on the 'Ordering' koan

It shouldn't matter what order resources in a catalog are executed, they should
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

