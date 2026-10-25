# Project Rules 

Here is a list of basic project rules for developers and AI Agents

----------------------------------------------------------------------------------------------

IMPLEMENTER RULES

- Split of concerns to differnet modules 
  - one of the most important rules
  - cascade in folders that match functionalities the software provides
  - cascaded software modules should be highly configurable via build config settings
  - module-based software composition whatever your build should include or exclude
  - always stay in the project structure or split modules further if it seems right

- Instead of comments the code should be highly human readable and therefor maintainable
  - code should be self explainable and human radable
  - code should be maintainable without AI

- Code and variable naming should be documented in documentation/glossar.md
  - You should always follow the project naming conventions
  - You can add project naming conventions and place them in the glossar.md
  - If somethings seems wrong you can add code marker "// NAMING-CHECK" to check later

- Code should have limited hardware ressources in mind
  - do not oversize variables
  - do not douplicate references unneccesaraly
  - do not douplicate helper function

- keep it simple if possible

- firmware security is a huge requirement
  - make your userinputs are validated and secure
  - you can always mention security concerns 
  - make sure and also check history that no personal information is commited to git
  - make sure and also check history that no secrets are commited to git

- Debugging
  - feel free to add modulewise debug logs and leave them there if you can exclude them from the build
  - debug logs should only be active in dev/experimental software maturities
  - feel free to add helpful logs to the user for flow logging in info logs


----------------------------------------------------------------------------------------------

SDK RESEARCHER RULES

- Before implementing you should consider if the used sdk is offering a solution than use this
- How to match best btw projects naming convention and sdk naming?
  - document this in a documentation/glossar.md where you should always have naming agreements
  - use this naming agreements on documentation, code and comment
  -  

----------------------------------------------------------------------------------------------

DOCUMENTATION RULES

- Code should have very limited amount of comments
  - If there is an explaination that is beyond a short comment add a link to the documentation path
  - Documentation should be in best case visulaized instead of a detailled markdown

- visualized documentation
  - whenever possible create a visual documentation with drawio.svg instead of a text
  - this svg should be integrated in the software architecture documentation
  - keep it simple and do not overload with text blocks
  - you should always refer to the documented sw version tag (textblock bottom right)
  - you should always refer to the documented date dd:mm:yyyy (textblock bottom right)

- There should be a single source of truth for docuemtation
  - best at projects root documentation/
  - split the documentation in software-documentation and hardware-documentation if needed
  - software architecture documentation needs a tree split format that matches the software
    - Exaples (interfaces/.., user-com/fault-handling, ....)



----------------------------------------------------------------------------------------------

GENERAL AI AGENT RULES

- You can setup agents with lighter models for better token efficency based on the task