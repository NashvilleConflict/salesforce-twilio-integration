# Music City Legal Hackathon

## Background: Nashville Conflict Resolution Center
- clients live lives of toxic stress
- volunteers are trained in trauma-informed care
- try to mediate cases out of court
- general sessions court:
  - like small claims court (< $25,000)
  - not a court of record (no one writing down)
  - judges rotate so they're unpredictable
  - lots of people are pro se (no legal representation)
  - show up and help people same day at court
  - most clients have landlord-tenant cases
  - lots of landlords actually care and want mediations
  - lots of tenants had medical emergencies or other issues paying
  - lots of elderly parents evicting their drug-addicted children
  - the court only touches the tip of the iceberg
  - but the mediation involves the rest of the iceberg

## Current Problem
- mediation often results in continuing the case, which requires the next court date
- the nonprofit wants to prevent punitive charges as much as possible
- continuance date can postpone the continuance if the are working
- but this requires paperwork filed by the plaintiff
- if NCRC calls both parties before the continuance then they usually return to the plan
- the plantiff is liable if they don't file the continuance and don't show up
- this gives them a bad reputation with the court

## Setup
- automate a text message 10 days before continuance date

## Ideas
- text's are lost, so facebook? what's app
- system should be able to communicate with various apps
- request a reply to confirm they're ready
- fast forms (salesforce) to fill out forms
- perhaps they could sign all the requests for continuance at mediation, so NCRC
- social media
- email
- provide a link in the text to fill out a form online
- filling out parenting plans and domestic violence forms with
- they also fill out forms at general sessions
- what goes in the 250 text?
- it's also hard to get follow-up data for funding
- request feedback 3 months later from clients
  - if they say it wasn't, then NCRC calls
- stack:
  - texts go out on twillio and come back on zapier (because twillio)
  - heroku

## Questions
- do they need carriers to send messages?
- are they collecting them?
- can they be looked up

- salesforce add-on: "volunteers for salesforce"
- volunteer job is an object representing a mediation
- each job can have associated activities
  - Zapier brings text
  - create new activity
  - 1500 people might be contacted

## Measures of Success
- saving money (or not spending more)
- documenting current process for future developers
- create a more user friendly way to send custom messages
- establish a more user friendly way to parse texts that return
