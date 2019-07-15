# Accross Departments

## What kinds of departments
How high up the reporting change are you looking to do?  Two development groups and an operations group.  How can you get more interaction with devops.  Sometimes there is a large amount of support and other times there is not.

Central IT and networking was also called out.

Digital library team and the general larger institution IT.

Non developers

Software engineers are spread, but operations is centralized.  Developers doing solo devops on Heroku.  And larger groups doing shared aws infrastructure
	Put all rails apps on the rails server vs make new vms for each application
	Started devops with platform as a service in the development world since central it was underwater
	Servers took 8  months to be built.  Then more people were hired with new skill sets.
	Push for non manually controlled machines
	Looked for someone who was interested vs making someone who was not interested in learning it.

What does it look like when an operations team is trying to keep their heads above water?
	Acted as the naive new person, to ask many questions to the operations team and peers.
	Failed to automate anything made it hard to keep up.  They did not have time to fix the issue.  Had not had the training to go forward.

Is devops motivated by trying to get away from old practices or getting more efficient?  
The answer is both are goals.

Development into the systems administration world.

Single developer with ITS, or projects that span university.  It is very hard to find the correct person who will help you do your joib.

## Problems that people have had

Operations were in control of everything and they had the time to work on it, so operations was in control of all technical decisions.  The decisions were not entirely useful for developers, since they did not know the tools.

Unless you are able to articulate what process is involved with creating the VM, you are allowed to think the other group of people are not meeting their needs.  Ansible speeds this up, but two days could be fine.  You could be out of a job unless you can define what you are providing.

Stakeholders desiring live servers every 3 hours.  That is not possible with automation or more resources.
How do you articulate the need for more resources? Need another person, S3, Isilon

How do you know how hard your request is can make it impossible to be thoughtful about their needs. 

Difficulty of simple requests from one perspective can be very difficult from another perspective.

Difficult things can also be easy.

## Things that people are doing well

Operations was not being transparent for the reasons for the no.  Transparency creates trust.

How do we make this happen in a way that works for everyone?  Can we get you most of what you need?

Ansible Fiesta and actual training about what and how you want things done.

Meeting other people where they are is the key to communicating.  Creating the channels and finding allies in a department.

## What are people doing about formal connections between teams? What structures that are supporting this?
Regular meetings between departments.  Monthly meeting.
Institution wide technology working group meeting.  Sometimes being able to vent is helpful.

Wished for: Departmental fire drills that say on a specific day we will take down a machine.  Orangelight staging will be shut down.  These are our pain points.  This is what it touches.  Gives you a clear understanding of what happens on the operations time.  Everyone sits together to figure out how to react. This is less stressful during an actual incident.  Additionally helps to share the burden.

During the urgent situation you may not know what things are happening.  Should we post a zoom link during an issue.

Post mortem reports for all incidences.  At the team meeting go over the results.

Being very clear about what channels that you have and inviting people to them.  We have a slack channel for talking to stakeholders, please use the slack channel.  Everyone is welcome to come to the standing meetings.

We have been utilizing a kanban board to make it obvious what is going on.  The operations team is not utilizing it.

Developers groups use kanban boards effectively, because there are multiple tasks people can do.  This can be just as useful in an operation context.

Kanban: Task management system, todo, doing, done.  Limits things you can have open.

It is hard to get in the mindset of breaking down very large tasks.  Not as used to breaking down tickets into smaller tasks that are easy to distribute.

Pair between development and operations team.  One person driving and another person talking.

Visual studio code has a live share feature.  Working on the same codebase and share who can work on it.

Pairing on new servers, and setting up ansible. Opportunity with a new project to share the decisions.  Knowledge sharing, and how other people approach problems.

Pairing is extremely rewarding, but maybe there are not as many opportunities.

Pairing started as an on site practice.  

Failed to get people to care about paired programming, because past interactions may have not been successful.   Remote might make it less weird to pair.

Pu library - ansible_fiesta https://github.com/pulibrary/ansible_fiesta

Pairing can be schedules do you are not just doing it when you are asking for help. 
It is good when we are pairing before the problems occur.  It makes it easier to work together when a problem does occur.

What are your ideas for asking people to learn about devops:
  Working one on one with developers.  I am you point person to get your thing off the ground.
  Training resources when people have asked for them.  One on one collaborative.
  Hope to connect with other developers in other departments.
  DevOps principles without containers.  Full configuration management
  Continuous integration is needed for everyone
  Luck with identifying small projects that we can work directly with another person. Targeted collaboration on smaller projects.
