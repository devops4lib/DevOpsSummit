#Soltuion Sharing

Why is this [finding and sharing solutions to technical problems] so hard? Why is everything hunting & gathering on your own?

Do our solutions fall into two baskets: 
* This is so obvious it’s not worth sharing?
* This is so obscure no one will ever care?

There’s no stackoverflow ‘4’  lib

Culture of Ops is that you can’t share deployment config for fear of exposing vulnerabilities (++)

...but Culture of Open Source says exposing vulnerabilities is good!!

Don’t make decisions in isolation! Exposing config to many eyes is good!

Developers are noisy (chatty) about their work… not so with Ops

Solution: invite interested (third) parties into private repo to inspect configuration docs?

Code review for docker config is valuable
Having validation from third parties that you’re doing things right

Stuck between the
Fear of being proven wrong
Arrogance of having to always be right

No reference builds for software deployments… If you want to have a working X instance, how do you build it? Nobody knows!

Problem: Varying toolchains… does Ansible have critical mass to become the default? 
Solution: Post standard solutions (roles) to Ansible galaxy?

Shared solutions need to find balance between flexibility and simplicity

Any shared solution is a good thing

Princeton published their solr config, Temple looks at it ALL THE TIME

Projects need more Ops documentation… lags behind dev documentation in projects like Samvera
Problem: documentation is developer focused

If documentation ends up in private github, does it need to be mirrored to public repo?
Software starts out as niches that grow into communities… maybe it’s on us to do that for Ops
Devs outnumber the Ops…

Different toolchains are an impediment to information sharing  (Puppet vs Ansible)

Problem: not knowing who’s using a similar stack/toolchain, and which github has the solution you can use

#DevOps slack needs to grow… doesn’t answer as fast as dev channels

You can still learn from deploy scripts written in a different toolchain


Is there hesitance to help out on ops because it takes away from your own work? Am I too busy? Does my boss sign off on this? Or is it part of our job?

The benefits to pairing/sharing are clear. You learn even while giving advice. You build a professional network. You give back.

For culture change breakout… Ops needs a culture shift to be more open.

Solution: Move to cloud provides opportunity for standardization… common vm, hardware

Solution: Only way to find out who’s on what cloud provider is to come out and meet other Ops

Islandora repo with a listing of all participating institutions and their installation details
https://github.com/Islandora-Labs/islandora_deployments 

Penn is doing this with their custom Dockerimage applications (currently internal), with an eye toward putting this on GitHub publicly.

Solution: Make community engagement explicitly part of the devops job description

Solution: More DevOps writeups in e.g. code4lib journal

Solution: Code4Lib stackoverflow?  But how to get critical mass?

Problem: We in libraries are too good at putting things in silos (hindering a common solutions community)

Problem: Questions answered in Slack are ephemeral

Solution: Weekly topic in #slack: “Share whatever it is you’re doing this week” ++
DevOps4Lib: “We Have A Blog”
https://devops4lib.github.io




