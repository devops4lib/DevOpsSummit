Note Taker: Francis
TImekeeper: Dan
Gatekeeper: Cole

## Testing infrastructure code

Infrastructure is whatever you use to launch your environment

Problem statement: Testing infrastructure is really slow

Ability to spin infrastructure on demand is expensive and slow

Molecule (Ansible) was easy because you are not breaking things. It is helpful because you are using containers.

Idempotency is also extremely painful however

CircleCi doesn’t work as well with molecule but Travis does. Cole promises to share the CircleCI tests with molecule.

Despite all the above Testing is worth it.

## A/B Testing

A/B testing is checking if your code actually improves things for the user in production

Use flipflop to do AB testing, and checking logs to see if people are opting in vs opting out

Re-playing recorded live traffic

A/B testing is similar to Canary Testing

Identifying users is done at random and directed by load balanced hardware.

Feed Apache JMeter logs to replay

Good a/b testing requires tight rollback procedure, clear monitoring.

### Tools:

https://www.nginx.com/blog/performing-a-b-testing-nginx-plus/

https://github.com/voormedia/flipflop

Apache JMeter (https://jmeter.apache.org/)

https://github.com/psu-stewardship/scholarsphere/tree/develop/benchmark



## Getting Feedback

What kind of user feedback:

Who are the users? What are our questions?

* Developers: is ansible working? Is molecule working for testing? Are you comfortable that you're able to solve your problem independently?
* End-user as a secondary / transitive concern.
* Library patrons: changed library catalog most aggressively, how is it succeeding? A UX team is a good place for this work to move forward.\
* Monitoring is another proxy for end-user feedback; in an ideal setup it pre-empts an end user and we respond quickly enough that we never need to hear from a user.
* How to user test an API? Work on documentation, solicit tickets.
