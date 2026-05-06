# FDE Flywheel

*Source: FDE Flywheel.pdf — Notes captured April 27, 2026*

Reference artifact: `Stryker_UseCase_Scoring_Template.xlsx`

---

## Steps for Intake

> Note: Probably out of order — these are things that should be in this process.

1. Intro the business to what FDE is and the purpose of the team, what to expect
2. Create context repo & add context
3. Deep dive meeting
	*Key questions to get answers to (NB: not an exhaustive list)*
	1. Who are we solving for?
	2. What are the jobs to be done?
	3. What differentiates the AI solution from the current state?
5. Fill out intake template based on deep dive; identify gaps in understanding & remaining questions
6. Prep data/tech spec specific to use case
7. Conduct shadow session with business users to fill gaps and inform solutioning
8. Identify reusable components that will be developed or leveraged as part of the prototype
9. Scope the prototype
	   - Identify the full scope (if this was productionized, what would it encompass)
	   - Decide what makes sense to break off (one data subset, one workflow step, lower threshold for accuracy, etc.)
10. Diagram the future state workflow
   - Show the roles, handoffs, AI integrations, inputs to the AI, AI outputs, review steps
10. Outline expected impact from full solution & from prototype
    - This does not include creating a detailed business case or drilling into all the stats around the current process — more so determining what a reasonable expectation of accuracy is and the automation that could result, the amount of time still required
11. Finalize intake template
12. Stage gate — make a determination around how to move forward *(may be determined earlier in the process)*
    - We should prototype: yes or no
    - We should get more requirements for scoping: yes or no
    - We shouldn't even bother building this: yes or no
13. Present the process to the business users to get alignment that the solution will actually address the need
14. Build prototype
15. Come up with a plan and estimate for productionizing the prototype

---

## Open Questions

- What is the final output of the prototyping exercise?
- What is the goal of the prototype? What should the prototype prove?


## Goals of "Prototype"

What should the prototype prove?

- Validate what we heard
- Validating what we see as the future vision
- Confirm requirements by getting business team's reaction
- Understand what else we need to know/prove out - scope follow-on prototype
- Support deeper scoping/deeper requirements solicitation
- Validate the expected impact (time savings, process improvements, reduced effort, etc.)
	- May require very high fidelity solution to mirror production benefits
- Validate technical feasibility 
	- Integrations
	- Data accessibility
	- AI feasibility & expected accuracy 
## Prototype Types

Action item - need better names
	Bones???? Joints????

- Type A - Ulna
	- 24-48 hour timebox
	- Scripted 
	- No integrations with data
	- No integrations with AI
	- Demonstrates a single user story/requirement
	- Not dependent on Stryker env
- Type B - Radius
	- 24-48 hours
	- No/minimal UI
	- "Technical spike"
	- Proves a single integration, single data activity, or single AI task 
	- Not dependent on Stryker env
- Type C - Metacarpal (or Forearm?)
	- 48-72 hrs
	- Multiple team skillsets involved (AI + CX)
	- UI 
	- Integrated with AI
	- Live interaction
	- Demonstrates a single user story/requirement
	- Requires connection to Stryker AI
- Type D - Brachium
	- 1-3 weeks  
	- Gated - will get signoff from Alfonso & team to make sure we should be spending this time
	- Stryker IT must be ready to accept this
	- Integrated with Stryker's data/systems
	- UI with live interaction
	- Demonstrates multiple requirements/user stories
	- Involves a pilot
	- Results in metrics to inform if this should move forward to production
		- Estimated time savings, accuracy, etc. 


Prototype (A, B, C) - > Dev MVP -> UAT/Piloting -> Production build


Notes from Nicole- should cross-check against this

Team, one thing I am observing with FDE engagements is a need for the internal team to define what a prototype is in terms of level of fidelity. You can determine the criteria, e.g. uses mock data versus a true sample set, has security credentials or other verification, more sophisticated technology (like OCR), etc; whatever you deem as a low/medium/high fidelity. Everything will be working code, but want to make sure you are aligned so that you know where to spend your time effectively. This is going to become vitally important as you start showing things to Alfonso, et al  - he may be happy with low lift examples to see that we are guiding the conversations with teams in the right direction. 

The other factor will be determining what's needed for the hand offs as you start working with engineering teams to take things to production, e.g. you may have to do a high fidelity version that engages with SSO, et al to make sure that it could be deployed. 

Btw, the FDE tiger team is trying to find a different word to use than prototype for the high fidelity versions, lmk if you have any suggestions  Prototype makes it sound more toss away than it will likely be in terms of working code.