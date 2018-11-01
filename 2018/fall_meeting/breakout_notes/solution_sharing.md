# Solution Sharing

Problem statement: Why is this so hard?

It feels like we (meaning Samvara-y libraries) should be doing things similarly but we're all doing things in different ways.
* Internal constraints / decisions made long ago: We have an internal cloud provider so we have to push hard to use external services
* Lack of confidence in the correctness of our solutions. E.g., this repo is private because we don't want anyone to see our code.
  * Sometimes we're advertising our solutions one way but they actually work differently
  * There's a practical side of this, where you don't want anyone less experienced to follow your lead
  * Fear of criticism, complicated by difficulty of understanding / conveying tone in writing
* requires vulnerability
* Tooling changes so fast that when you start solving your problem the set of solutions is much larger than it was the last time someone in the community did it
* Similar to the reason documentation is hard: we're busy doing the work
  * there's no time to stop and say "it's done, time to share / document"
* People mistake sharing for a security risk
  * Or even just keep everything private just in case there might be a secret in there
    * It's hard to scrub secrets from configuration management code; you do have to be very careful
    * You have to follow changes in best practices in case best practice changes and you need to change your code
    * Example: public-first configuration with CI/CD means you have to give secrets to CI but you can't allow a build from a fork because someone could echo your secrets.
  * But sometimes exposing solutions leads to better security because you can get feedback
    * although just because something is public doesn't mean it is audited
  * better secrets management can mitigate this tendency

Idea: Consortium with a private repo with configuration code that we work together to audit / review code.
* legal concerns here to build a consortium. individuals have contracts with different organizations to protect their data / org.
* Just open sourcing it to the public might be an easier sell

Why aren’t we using the blog we created this summer?
* This has more longevity than email, slack messages. Good place to put solutions for posterity.
* Make sure credentials are easy to obtain
  * hint: submit a PR to github.com/devops4lib/devops4lib.github.io
* Sometimes a screencast might be easier than a write-up

What other ways can we share solutions beyond just sharing our code?
* Larger scale: more abstract questions, approaches, concerns (scaling, security, data robustness)
* Smaller scale: I feel like I solve little problems all the time (e.g. where ansible doesn't work the way I expected it to) and I think "I should share this! But where?" (see: blog, above)
* Some way to convert high-participation slack conversations into github or blog posts?

What are we already doing well?
* We met 3 times in 1 year
* We tell each other what we're up to every week. How is this going?
  * We have a good sense of who's doing what, who to reach out to. E.g. "I have a note to myself, 'when we start doing X I should reach out and ask Chad to have a brief call with me'"

Resolved: to write more blog posts! People who have volunteered to write blog posts:
* Drew
* Nick
* Chad: D&D-style training
* Erin: The CI/CD secrets management conundrum "Secrets management concerns in hosted management CI"

Ideas / action items:
* Add a day to this gathering where we pair to review one anothers' solutions / configuration code, etc.
* purchase a top-level domain for our blog (Erin volunteered)
* program a slack bot to "blog this" from slack
* put blog info on readme of our primary github repo
* Set a slack reminder to prompt people to post to the blog (include pointer to documentation on how to do this)
* Add a README to https://github.com/devops4lib/devops4lib.github.io with instructions, pointers to jekyll documentation. (done!)
