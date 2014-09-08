#

2009 start building monolith.
2012 begin building 2nd service - 3 person team at the time.
gradually added 3 more people since then
some use MySQL, some user Postgres 1 uses Mongo
- much easier to use the right tool for the job
152 total repos
  2 legacy codebases
  24 web apps & services
  4 supporting web services (error logging, hosting dependencies, monitoring)
  2 applications
  13 client libraries
  47 libraries
  60 misc repos
recently changed framework used for a central system
  - extremely painless
  - had good "integration" tests
- Extract Services, Libraries, Applications
- Create Adapters (an adapter could be a service, library or application)
- Challenges
  - security (signed requests)
  - versioning - use semver - lock in specific versions
  - api changes - try to not make backwards incompatible changes
  - integration tests - can be daunting - CAN be somewhat unreliable
    - make sure certain system's tests don't run at the same time...
      - jenkins plugin for that
  - Deployments (need to automate - because you'll have more)
  - Server Provisioning (need to automate - because you'll have more)
- Benefits
  - Everybody gets to work in their own codebase and not worry about merge conflicts
  - Deployments are simple and low risk
  - Each system is much smaller easier to digest and get your head around
  - Lots of opportunities to evolve tech stack
  - Projects are smaller - much easier to "re-write" systems
  - Forces you to build APIs and not bury data
    - Allows use of Front End JS MVC frameworks to leverage APIs
  - can make system more flexible and more reusable
    - Rating
    - Imaging
    - Workflow

Rating -
  - process
    - old system & new system talk directly to each other
    - unreliable technology
    - wrap old system with http api
    - works great
    - purchase new "legacy" system - need new system to talk to it also
    - currently new system is riddled full of stuff specific to old system
    - move it all to the old system api wrapper
    - everything still works great
    - build general "adapter" in the middle of new system and old system api
    - everything still works great
    - add new API around purchased "legacy" system
    - have adapter fork to talk to legacy system 1 or 2 depending on customer
    - everything still works great with old system and we now integrate with a new system

  2 legacy rating systems
  1 new web based UI
  didn't want to rewrite a new rating engine
    - wanted to avoid (I get $X in the old system but $Y in the new)
  Wrap each legacy system with an api
  wrap the legacy systems' APIs with an api
  new web based UI talks to that API
  - adapters
