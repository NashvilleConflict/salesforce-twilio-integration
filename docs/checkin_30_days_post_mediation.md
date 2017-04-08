# High level
The last hackathon (at HCA on 2016.10.14) created a way to trigger a text message 30 days after a mediation to get feedback from the plaintiff / defendant

However, they didn't document this process, so we're (at the MC legal Hackathon 2017.04.08) documenting it here. We have ideas about how to improve it, but that will be documented elsewhere (in this source code repository).

# Process
- a user marks a mediation as "Completed" in Salesforce
- this triggers custom Apex (java-based proprietary salesforce language) code to make an API call to Twilio
- Twilio sends text message to client (SMS)
- text comes back through Twilio to Zapier
  - configuration is a job in Zapier to receive the text (via Twilio), and send the data (including the text body) to create a new a "Completed Activity" in Salesforce
  - this configuration job is called Create <entity> Response with the following entities:
    - Defendant 1
    - Defendant 2
    - Plaintiff 1
    - Plaintiff 2
  - lands inside the Salesforce custom object type called "VolunteerJob"
  - there will be one object for each case, for example, "Jane vs. Henry"
  - the text response will be recorded in the VolunteerJob (i.e. case) as an Activity (under "Activity History" subsection) with a title such as "Defendant 1 Text Response - No" (the text after the hyphen is the text message body, e.g. "No")

# Navigating Salesforce (to src)
There are lots of objects in Salesforce that appear relevant, but we believe they are actually red herrings from prior attempts etc. Many are not even activated.

Here's how to find the code:
salesforce > apex classes >

- setup (top menu right side)
- type "apex classes" in left side bar search bar (directly below the top-left icons)
- You want to find the rows in the table with "Sara Fingal, 10/14/2016 12:49 PM" in the `Last Modified By` column
  - you can do this by sorting the column (`Last Modified By`) descending Z-A and click through pages to find "Sara..."
  - or you could select the "S" shortcut to the top left of the table to see the rows starting with "S"
    - (you will still need to sort for this to work so that it looks for "S" in that field)
- see 5 jobs
  - 3 messages types
    - use "SendTextMessage"
    - (the other 2 are tests)
  - VolunteerJobScheduler
  - VolunterBtach (yes that's the current spelling)

Congratulations, you found the code (that took us a whole day)!

## Next Steps
You can "clone" (look for the button) this Apex class to create similar triggered messages.

However, there are probably much better ways. We will produce separate documentation for our ideas about better way to do this elsewhere, but this shows what **works** today.
