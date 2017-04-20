How to contribute
=================

Thank you so much for wanting to contribute to CDBC! Here are a few important things you should know about contributing:
  1. API changes require discussion, use cases, etc. Code comes later.
  2. Pull requests are great for small fixes for bugs, documentation, etc.
  3. Work with repo maintainers to get your change reviewed.
  4. Code contributions require signing a Contributor License Agreement.
  5. Delete your feature branch once the development is complete.


API changes
-----------

We make changes to CDBC's public APIs, including adding new APIs, very carefully.
Because of this, if you're interested in seeing a new feature in CDBC, the best approach is to create an issue (or comment on an existing issue if there is one) requesting the feature and describing specific use cases for it.

If the feature has merit, it will go through a thorough process of API design and review. Any code should come after this.

Pull requests
-------------

Unless the change is a trivial fix such as for a typo, it's generally best to start by opening a new issue describing the bug or feature you're intending to fix.
Even if you think it's relatively minor, it's helpful to know what people are working on. And as mentioned above, API changes should be discussed thoroughly before moving to code.

Some examples of types of pull requests that are immediately helpful:
  - Fixing a bug without changing a public API.
  - Fixing or improving documentation.
  
Guidelines for any code contributions:
--------------------------------------

  1. Any significant changes should be accompanied by tests that are easy to read and execute. The project already has good test coverage, so look at some of the existing tests if you're unsure how to go about it.
  2. All contributions must be licensed Eclipse Public License 1.0 and all files must have a copy of the boilerplate licence comment (can be copied from an existing file).
  3. Files should be formatted using clang-format with the style configuration found in the project.
  4. Please squash all commits for a change into a single commit (this can be done using `git rebase -i`). Do your best to have a [well-formed commit message][] for the change.
  5. Remember not to add sensitive/confidential data such as hard-coded passwords, client information, email addresses etc.
  6. Remove legacy code (and tests) where possible to keep the codebase clean.
  7. Any contribution must not contain, nor must be accompanied by:
   - materials not created by you, or source code or other materials which result in the inclusion of third party materials;
   - materials that would be considered confidential and/or proprietary information, or trade secrets owned by you or third parties;
   - your, our, or a third party’s, internal data, whether or not considered confidential and/or proprietary, e.g., intranet URLs, internal emails, client information or references to the foregoing;
   - materials which practice, or require the practice of, a patent owned or controlled by a third party, or a proprietary standard, specification, protocol, algorithm, or the like;
   - software or other materials which are known to be the subject of an actual or threatened patent infringement or other legal claim;
   - software which may be subject to export control laws or regulations;
   - trademarks, or software which generates trademarks;
   - nonpublic personal information, or personally identifying information generally (e.g. employee names), or information regulated or controlled by data privacy laws and regulations;
   - product code names, roadmaps, future product descriptions;
   - disparaging comments;
   - viruses or other malicious components (including “back doors”, “time bombs”, “logic bombs”, “Trojan horses”, “worms”, “drop dead devices”, “viruses”, “trap doors”, “timers”, “clocks”, “counters” or similar), or any other computer software routine intended or designed to disable, damage, erase, disrupt or impair the normal operation of, or provide unauthorized access to, computer systems or any software or information stored on those computer systems;
   - SSH private keys or passwords, or authentication means generally;

Merging pull requests
---------------------

Once a pull request is ready for merging, we'll merge the appropriate changes in the internal codebase.

Contributor License Agreement
-----------------------------

If you are not currently employed by Murex, or if your contribution was created outside of the scope of your work at Murex, you must have entered into a contribution agreement with Murex which governs your contribution.  

Please email one of the project owners for access to such agreements.

You generally only need to submit a CLA once, so if you've already submitted one (even if it was for a different project), you probably don't need to do it again.