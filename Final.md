### Study guide

Review slides, notes taken during tech talks, and workshop materials. This is a comprehensive exam over the entire class.

Everyone in the course is expected to be capable of the following course objectives and demonstrate them in a written exam:

* Understand **core terms and principles** related to continuous deployment and devops.
* Programmatically **provision** images.
* Automatically apply **configuration management** to production environments.
* Automatically create and maintain **build** environments.
* Maintain test suites and measure **testing quality** and coverage.
* Automatically **generate new tests**, using feedback-directed random testing, fuzzing, and data-flow analysis.
* Programmatically measure **code quality** via static and dynamic code analysis.
* Understand components of **infrastructure**.
* Remotely regulate behavior of deployed software via **feature flags** and configuration servers.
* Apply advanced strategies for **deployment** of software.
* Monitor and analyze **telemetry** data.
* Implement **resilience testing** on production environments (e.g., Chaos Monkey).


The following are example questions that will be similar to questions you will have on your final exam. Note that the actual exam will be much longer in length.

### Multiple Choice

1. Which tool or service best represents: *virtualization*.

  * A) Ansible
  * B) NewRelic
  * C) Mocha
  * D) Vagrant

2. Which of the following best describes a *mutation-based* fuzzing technique:

  * A) Test input is randomly modified.
  * B) The test input can be based on existing examples.
  * C) Both A and B
  * D) Test input is created by grammars.
  * E) All of the Above

3. Which definition best describes *continuous deployment*:

  * A) A practice where developers automatically build, test, and analyze a software change in response to every software change committed to the source repository.
  * B) A practice that ensures that a software change can be ready for use by a customer by testing in production-like environments.
  * C) A practice where incremental software changes are automatically tested, vetted, and deployed to production environments.
  * D) B or C
  * E) None of the Above

4. What term best describes the following: "Developers may manually prevent access to parts of production systems, while they are performing deployments".

  * A) Rolling Updates
  * B) Operation Locks
  * C) Expand and Contract
  * D) Big Flip
  * E) Feature Flags

### Definitions

1. Which tool or service does not belong with the other? Underline one choice per line. (1 point each).

  * Docker, Vagrant, Chef
  * Ansible, Salt, Puppet, Otto 
  * Jenkins, HAProxy, GoCd, SnapCI
  * npm, bower, mocha, maven, ant
  * OpenStack, AWS, Rackspace, Kubernetes
  * Grunt, Fuzzing, Randoop
  * Docker Compose, Fig, Decking.io, Digital Ocean
  * Redis, Memcached, CruiseControl
  * NewRelic, Flame Graphs, Simian Army
  * Chaos Monkey, Splunk, Canaries

2. Describe two simple ways to detect duplicated code during static analysis.

3. List three issues related to Canary Releases. Additionally, name one alternative that achieves a similar goal.

4. List three stages in the Nygard Monitoring Framework.

### Scenarios

1. A company has each developer create a seperate branch to work on their feature that they deploy. They often face delays merging code together and have difficulty rollbacking deployed features. What practice if introduced might help?

2. A system has a lot of test cases. Every time a change is made, it takes a lot of time to run the test cases. How will you ensure that test cases run fast and developer gets timely feedback about the same?

### Implementation

1. Measure branch coverage of a code snippet.

  **Test suite**:
  
  * weird(0, 0, 0, "strictly")
  * weird(88, 42, 42, "stricter")
  
  ```Javascript
  function weird(x,y,z, mode, results)
  {
      if( x > 87 && y < 70 )
      {
          z = 33;
          results[0] = inc().data[0].fetch().cached.first.name;
      }    
      else if( z < 42 )
      {
          if( mode == "strictly" )
          {
              return 0;
          }
      }
      else
      {
          if( mode != "stricter" )
          {
              results[1] = inc().cachedResults;
              return y = z / x;
          }
      }
      return 1;
  }  
  ```

2. Write a parser using a simple visitor pattern to count the number of ifs in a function.

### Discussion

1. Compare and contrast using Kubernetes versus plain AWS for your production environment. List two benefits and two disadvantages of each. Justify differences. *Finally, describe how they might work well together*.

### Design

1. Design a deployment pipeline. Describe what commands would be needed to run inside each stage. Describe the infrastructure of the production environment. *Focus on creating a well annotated diagram, paragraphs of text will not count*.
