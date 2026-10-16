# CS6983 - HW1: Prompt Pairs, Proven

**Qiong Wu**

## 1. Setup

My plan is to test three different prompt types, based on my Project 1, World Cup Fan Timeline Calendar

- Generate: Create a UI component that allows users to add flight information to their World Cup travel timeline.

- Extract: Create a prompt that can convert flight confirmation Email into valid structured JSON that can be directly used by the UI component from the Generate task.

- Critique

For each experiment, I will follow several steps

1.  Create a checklist with 4–6 pass/fail items that can score the prompts

2.  Write a realistic, bad prompt

3.  Write a better prompt improved by improving the bad prompt.

4.  Predicting the scores I expect for both prompts

5.  Run each prompt 3 times in a separate fresh chat and save screenshots

6.  Error analysis

7.  Verdict

I will keep following setting the same across all runs:

- Model: Claude Opus 5.5

- Effort level: medium

- Thinking setting: Always on

- Connector search: OFF

## 2. Three Prompt Pairs

### 2.1 Generating a UI component

I will write prompts to create a UI component for my Project 1 that allows users to enter their flight information, including departure, destination, terminals, flight number, seats, date, and time. The flight information will then be added as an event to the user's World Cup travel timeline.

1.  Checklist

    1.  Required field: the UI have inputs for departure, destination, departure terminal, arrival terminal, flight number, seat, departure/destination date and time.

    2.  Validation: the UI checks required inputs before save.

    3.  Date time validation: the UI check time are valid based on arrival date time cannot be less then depart time.

    4.  Departure – destination check: the UI check departure city is not as same as destination city

    5.  Readable format: every input has a clear label, and the user can understand what information should be entered without needing additional instructions

    6.  Output JSON format: After the user saves the flight information, the JSON can be easily reviewed and inserted into the database without reformatting

2.  Bad prompt:

Create a UI component that save my flight information including departure city, departure airport, destination city, destination airport, terminals, flight number, seats, date and time and output a JSON

3.  Better prompt:

Create a UI component that allows a user to enter and save flight information. The form must include: Departure city, Departure airport, Departure terminal, Destination city, Destination airport, Arrival terminal, Flight number, Seats, Departure date and time, Arrival date and time.

The UI should have clear label and easy input fields, a save button, all fields except seats are required, validating date time based on arrival date time cannot be less then depart time, validating that departure city is not as same as destination city.

There is a saving button, after I click the button, show a clear error message if validation fails,

there is a section displays the generated JSON, the JSON structure is:

{

"departureCity": "San Francisco",

"departureAirport": "SFO",

"departureTerminal": "Terminal 1",

"destinationCity": "Dallas",

"destinationAirport": "DFW",

"arrivalTerminal": "Terminal 1",

"flightNumber": " F9 4000",

"seats": "25E",

"departureDateTime": "2026-06-17T12:32",

"arrivalDateTime": "2026-06-17T06:10"

}

WHY Better:

The better prompt is better because it gives a clearer Task by specifying the required fields and validation rules. It also provides a clear Format by showing the exact JSON structure I expect. In addition, it includes Constraints, such as requiring validation and checking specific conditions like the arrival time being later than the departure time and the departure city being different from the destination city.

4.  Prediction:

Bad prompt will score 3.5/6: 1, 5 can be passed, I don't think it can pass 2, 3, 4. 6 is doubtful, it can result a JSON but I do not think it will format it well

Better prompt will score 6/6

5.  Evidence


1)  First run of bad prompt

> <img src="./media/image1.png" alt="Evidence screenshot 1" /> <img src="./media/image2.png" alt="Evidence screenshot 2" />

| **Checklist item**            | Score | Reason                                  |
|-------------------------------|-------|-----------------------------------------|
| Required field                | 0     | missing arrival date and time           |
| Validation                    | 0     | no validation                           |
| Date time validation          | 0     | no validation                           |
| Departure – destination check | 0     | no validation                           |
| Readable format               | 1     | format is readable, clear, easily input |
| Output JSON format            | 1     | result JSON is valid                    |

2\) Second run of bad prompt

> <img src="./media/image3.png" alt="Evidence screenshot 3" />
>
> <img src="./media/image4.png" alt="Evidence screenshot 4" />

| **Checklist item**            | Score | Reason                                                                                                                                                                                                                           |
|-------------------------------|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Required field                | 0     | missing arrival date and time                                                                                                                                                                                                    |
| Validation                    | 1     | It has validation                                                                                                                                                                                                                |
| Date time validation          | 0     | no validation                                                                                                                                                                                                                    |
| Departure – destination check | 0     | no validation                                                                                                                                                                                                                    |
| Readable format               | 0     | the layout is confusing. The flight number, date, and time fields are placed below the “Save Flight” button. I filled in the fields above the button and clicked Save Flight, but the UI displayed “Flight number is not valid.” |
| Output JSON format            | 1     | result JSON is valid                                                                                                                                                                                                             |

2)  Third run of bad prompt

> <img src="./media/image5.png" alt="Evidence screenshot 5" /> <img src="./media/image6.png" alt="Evidence screenshot 6" />

| **Checklist item**            | Score | Reason                                  |
|-------------------------------|-------|-----------------------------------------|
| Required field                | 0     | missing arrival date and time           |
| Validation                    | 2     | It has validation                       |
| Date time validation          | 0     | no validation                           |
| Departure – destination check | 0     | no validation                           |
| Readable format               | 1     | format is readable, clear, easily input |
| Output JSON format            | 1     | result JSON is valid                    |

3)  First run of better prompt

> <img src="./media/image7.png" alt="Evidence screenshot 7" /><img src="./media/image8.png" alt="Evidence screenshot 8" />

| **Checklist item**            | Score | Reason                                                            |
|-------------------------------|-------|-------------------------------------------------------------------|
| Required field                | 1     | Have everything I wanted                                          |
| Validation                    | 1     | Has validation                                                    |
| Date time validation          | 1     | Has validation of arrival time cannot earlier then departure time |
| Departure – destination check | 1     | Has validation of departure and destination city are not same     |
| Readable format               | 1     | format is readable, clear, easily input                           |
| Output JSON format            | 1     | result JSON is valid                                              |

> But it do not have previous records that can be edited and reviewed, which implemented in second and third run of bad prompt

4)  Second run of better prompt

> <img src="./media/image9.png" alt="Evidence screenshot 9" /> <img src="./media/image10.png" alt="Evidence screenshot 10" />

| **Checklist item**            | Score | Reason                                                            |
|-------------------------------|-------|-------------------------------------------------------------------|
| Required field                | 1     | Have everything I wanted                                          |
| Validation                    | 1     | Has validation                                                    |
| Date time validation          | 1     | Has validation of arrival time cannot earlier then departure time |
| Departure – destination check | 1     | Has validation of departure and destination city are not same     |
| Readable format               | 1     | format is readable, clear, easily input                           |
| Output JSON format            | 1     | result JSON is valid                                              |

6)  Third run of better prompt

> <img src="./media/image11.png" alt="Evidence screenshot 11" />
>
> <img src="./media/image12.png" alt="Evidence screenshot 12" />

| **Checklist item**            | Score | Reason                                                            |
|-------------------------------|-------|-------------------------------------------------------------------|
| Required field                | 1     | Have everything I wanted                                          |
| Validation                    | 1     | Has validation                                                    |
| Date time validation          | 1     | Has validation of arrival time cannot earlier then departure time |
| Departure – destination check | 1     | Has validation of departure and destination city are not same     |
| Readable format               | 1     | format is readable, clear, easily input                           |
| Output JSON format            | 1     | result JSON is valid                                              |

6.  Error analysis

All bad prompt failed on 1) Required field: the UI have inputs for departure, destination, departure terminal, arrival terminal, flight number, seat, departure/destination date and time. There are only departure date and time from bad prompt. And all better prompts have both departure datetime and arrival datetime.

**Failure category:** **Missing Format and too literally**

It is because the LLM took my prompt too literally, I input *date and time* but did not specify both departure and arrival.

One important item I wish I had included in my checklist is keeping and editing records. In my actual project, users need to keep saved flight records and edit them later, so this is an essential function of the flight UI. My checklist did not evaluate whether the generated component preserved saved records or allowed users to modify them. Interestingly, two of the bad-prompt runs included this functionality anyway, but because it was not part of the original checklist, I cannot add it to the scores afterward.

7.  Verdict

| **Prompt** | **Run 1** | **Run 2** | **Run 3** | **Average** |
|------------|-----------|-----------|-----------|-------------|
| Bad        | 2/6       | 2/6       | 3/6       | 2.3/6       |
| Better     | 6/6       | 6/6       | 6/6       | 6/6         |

the better prompts were better. They passed all checklist and follow all my requirements.

I expected the bad prompts to pass 1) Required Fields, but none of the three bad-prompt runs included all required fields. I also did not expect the bad prompts to include validation, but two of the three runs did include some validation.

However, keeping and editing records function was never implemented by better prompt but two bad prompts included.

### 2.2 Extract

Instead of entering all flight information manually through the UI, I want the LLM to read a flight confirmation email and extract the important details into structured JSON. The JSON should contain the flight information needed by my UI component and be directly importable into the application without requiring the user to retype everything.

1.  Checklist

    1.  Contain basic information: the LLM can capture some basic information: departure, destination, departure terminal, arrival terminal, flight number, seat, departure/destination date and time.

    2.  Capture all information: the LLM capture all useful information: Departure city, Departure airport, Departure terminal, Destination city, Destination airport, Arrival terminal, Flight number, Seats, Departure date and time, Arrival date and time. If any of these fields cannot be extracted from the email, the output clearly identifies which information is missing.

    3.  Irrelevant information ignored: the result does not include unrelated email content such as advertisements, promotional messages, loyalty program information, payment details, or general airline notices.

    4.  No fake information: the output must be as same as the email; it can remain empty.

    5.  Information mapped correctly: each extracted value is placed in to correct JSON field

    6.  Valid JSON structure: The response is valid JSON with consistent field names and can be parsed without manually fixing syntax.

2.  Bad prompt:

Extract information from my flight confirmation email output a JSON

3.  Better prompt:

I am building a World Cup travel timeline application. I want to extract the information from a flight confirmation email and convert it into JSON that my application can use. Extracting these fields when they appear in the email:

\- Departure city

\- Departure airport

\- Departure terminal

\- Destination city

\- Destination airport

\- Arrival terminal

\- Flight number

\- Seat

\- Departure date and time

\- Arrival date and time

Return valid JSON object using exactly these field names:

{

"departureCity": "",

"departureAirport": "",

"departureTerminal": "",

"destinationCity": "",

"destinationAirport": "",

"arrivalTerminal": "",

"flightNumber": "",

"seat": "",

"departureDateTime": "",

"arrivalDateTime": ""

}

Constraints:

\- Use only information that appears in the confirmation email.

\- Do not guess or invent missing information.

\- If a value is not provided in the email, use an empty string.

\- If a value is not provided or miss mapped, show a notification.

\- Make sure each value is mapped to the correct JSON field.

\- Do not Irrelevant information

\- The final response must be valid JSON that can be parsed directly.

WHY Better:

The better prompt is better because it gives a specific context, clear Context, a specific Task, an exact JSON Format, and detailed Constraints. It tells the model exactly what information to extract, what to ignore, how to handle missing values, and how to structure the final JSON, which should make the output more accurate and consistent.

4.  Prediction:

Bad prompt will pass 1, 4, 5, 6, and average score is 4/6. I don’t think it can capture all information I wanted, or there will be statement. Also, a lot of useless information may be contained.

5.  Evidence


1)  First run of bad prompt

[View Bad Prompt Run 1 JSON](media/bad-run-1.json)
> <img src="./media/image13.png" alt="Evidence screenshot 13" /><img src="./media/image14.png" alt="Evidence screenshot 14" />
>
> <img src="./media/image15.png" alt="Evidence screenshot 15" />

| **Checklist item**             | Score | Reason                                                                 |
|--------------------------------|-------|------------------------------------------------------------------------|
| Contain basic information      | 1     | Contain basic information                                              |
| Capture all information        | 0     | Terminals, seats are missing, and no notification                      |
| Irrelevant information ignored | 0     | Too many irrelevant information                                        |
| No fake information            | 1     | No made up info                                                        |
| Information mapped correctly   | 1     | Mapped correctly                                                       |
| Valid JSON structure           | 1     | Although it produced an overly nested JSON structure, but it is valid. |

2)  Third run of bad prompt

[View Bad Prompt Run 2 JSON](media/bad-run-2.json)
> <img src="./media/image16.png" alt="Evidence screenshot 16" />
>
> <img src="./media/image17.png" alt="Evidence screenshot 17" />

| **Checklist item**             | Score | Reason                                                                 |
|--------------------------------|-------|------------------------------------------------------------------------|
| Contain basic information      | 1     | Contain basic information                                              |
| Capture all information        | 0     | Terminals, seats are missing, and no notification                      |
| Irrelevant information ignored | 0     | Too many irrelevant information                                        |
| No fake information            | 1     | No made up info                                                        |
| Information mapped correctly   | 1     | Mapped correctly                                                       |
| Valid JSON structure           | 1     | Although it produced an overly nested JSON structure, but it is valid. |

3)  Third run of bad prompt

[View Bad Prompt Run 3 JSON](media/bad-run-3.json)
> <img src="./media/image18.png" alt="Evidence screenshot 18" />
>
> <img src="./media/image19.png" alt="Evidence screenshot 19" />

| **Checklist item**             | Score | Reason                                                                 |
|--------------------------------|-------|------------------------------------------------------------------------|
| Contain basic information      | 1     | Contain basic information                                              |
| Capture all information        | 0     | Terminals, seats are missing, and no notification                      |
| Irrelevant information ignored | 0     | Too many irrelevant information                                        |
| No fake information            | 1     | No made up info                                                        |
| Information mapped correctly   | 1     | Mapped correctly                                                       |
| Valid JSON structure           | 1     | Although it produced an overly nested JSON structure, but it is valid. |

4)  First run of better prompt

> <img src="./media/image20.png" alt="Evidence screenshot 20" />
>
> <img src="./media/image21.png" alt="Evidence screenshot 21" />

| **Checklist item**             | Score | Reason                         |
|--------------------------------|-------|--------------------------------|
| Contain basic information      | 1     | Contain basic information      |
| Capture all information        | 1     | Missing information is noticed |
| Irrelevant information ignored | 1     | No irrelevant information      |
| No fake information            | 1     | No made up info                |
| Information mapped correctly   | 1     | Mapped correctly               |
| Valid JSON structure           | 1     | Valid JSON.                    |

5)  Second run of better prompt

> <img src="./media/image22.png" alt="Evidence screenshot 22" />
>
> <img src="./media/image23.png" alt="Evidence screenshot 23" />

| **Checklist item**             | Score | Reason                                                                 |
|--------------------------------|-------|------------------------------------------------------------------------|
| Contain basic information      | 1     | Contain basic information                                              |
| Capture all information        | 1     | Terminals, seats are missing, and no notification                      |
| Irrelevant information ignored | 1     | Too many irrelevant information                                        |
| No fake information            | 1     | No made up info                                                        |
| Information mapped correctly   | 1     | Mapped correctly                                                       |
| Valid JSON structure           | 1     | Although it produced an overly nested JSON structure, but it is valid. |

6)  Third run of better prompt

> <img src="./media/image24.png" alt="Evidence screenshot 24" />
>
> <img src="./media/image25.png" alt="Evidence screenshot 25" />

| **Checklist item**             | Score | Reason                                                                 |
|--------------------------------|-------|------------------------------------------------------------------------|
| Contain basic information      | 1     | Contain basic information                                              |
| Capture all information        | 1     | Terminals, seats are missing, and no notification                      |
| Irrelevant information ignored | 1     | Too many irrelevant information                                        |
| No fake information            | 1     | No made up info                                                        |
| Information mapped correctly   | 1     | Mapped correctly                                                       |
| Valid JSON structure           | 1     | Although it produced an overly nested JSON structure, but it is valid. |

6.  Error analysis

All three bad prompt runs failed Irrelevant information ignored. The JSON outputs were much longer than necessary and contained many sections that were not useful for my World Cup timeline. Irrelevant information included: payment, policies, etc., Only the flight-related information was useful for my project.

**Failure category:** **Missing Format.**

One item I wish I had included is multi-flight trip. A single trip may include more than one flight. I want each flight segment to be extracted as a separate flight record instead of combining multiple flight numbers into one field. Separating the flights would make the JSON clearer, easier to read, and easier to use in my timeline application.

7.  Verdict

| **Prompt** | **Run 1** | **Run 2** | **Run 3** | **Average** |
|------------|-----------|-----------|-----------|-------------|
| Bad        | 4/6       | 4/6       | 4/6       | 4/6         |
| Better     | 6/6       | 6/6       | 6/6       | 6/6         |

The better prompt was clearly better than the bad prompt. My prediction is correct; all bad prompt failed on Capture all information and Irrelevant information ignored.

### 2.3 Critique prompt to improve UI component

I will use the HTML file generated by the third run of the better prompt in the Generate task as the input. I will ask Claude to critique the existing component and identify problems that could make the flight-information form more usable, readable, and clear for users. I have already identified four defects in the current component:

- No saved-record management: There is no section where users can review, edit, or delete previously saved flight records.

- No time-zone information: Departure and arrival times do not clearly show their time zones, which can be confusing when traveling between different cities.

- No multi-flight support: A trip may contain multiple flight segments, such as connecting flights, but the current component only handles a single flight record.

- No import section: There is no section that allows users to import extracted flight information, such as JSON generated from a flight confirmation email.

Checklist

1.  Implement the new version in artifacts

2.  Record management defect found and fixed

3.  Time-zone defect found and fixed

4.  Multi-flight defect found and fixed

5.  Import function defect found and fixed

6.  Other problems found or fixed

7.  Suggestion: there will be some specific and practical suggestions or and further advice.


1.  Bad prompt:

I created a UI component that saves my flight information. Can you review it and or suggestions. (attached HTML)

2.  Better prompt:

I am building a World Cup Fan Timeline Calendar for users who travel to attend World Cup matches in person. The attached HTML file is a flight-information UI component that allows users to add flight details to their travel timeline.

Please Critique the existing component and identify usability, functionality, and data-handling problems that could make it easy for a traveler to use.

I detected some defect and help me fix them:

\- No saved-record management, there should be a record section that user can review and edit records

\- No time-zone information: Departure and arrival times do not clearly show their time zones, which can be confusing when traveling between different cities.

\- No multi-flight support: A trip may contain multiple flight segments

\- No import section: There is no section that allows users to import extracted flight information, such as JSON

Fix the listed defects and improve if you can by apply artifacts

For other problem you find, provide:

1\. Problem: what is wrong or missing;

2\. Why it matters: how it affects the traveler;

3\. Improvement: a specific change that would fix or improve it.

Focus on practical issues that would affect a real traveler. Do not rewrite the entire component. Prioritize the most important problems and give actionable suggestions.

WHY Better:

The better prompt provides clear Context, a specific Task, and a structured Format for the critique. It tells Claude to evaluate usability, functionality, realistic travel situations, data handling, and the overall user workflow without directly giving away the known defects. It also requires Claude to explain why each issue matters and provide an actionable improvement, which should produce a more useful and complete critique.

3.  Prediction:

Bad prompt will score 4/7, passing 1, 2, 6, 7. I expect it show the new version with modification in artifacts, Because it was found defect 2 in previous section, I’m expecting it will find it too. And I also expect it find other problem.

Better prompt will score 6/6 because enough context is given, more specific task is listed. And further expectation is mentioned

4.  Evidence


1)  First run of bad prompt

> <img src="./media/image26.png" alt="Evidence screenshot 26" />
>
> <img src="./media/image27.png" alt="Evidence screenshot 27" />
>
> <img src="./media/image28.png" alt="Evidence screenshot 28" />
>
> <img src="./media/image29.png" alt="Evidence screenshot 29" />

| **Checklist item**                 | Score | Reason                                   |
|------------------------------------|-------|------------------------------------------|
| show in artifacts                  | 0     | just simple text, no artifacts           |
| record management                  | 1     | found save problem and give suggestions  |
| time-zone added                    | 1     | detect timezone bug                      |
| multi-flight function added        | 0     | Not found                                |
| import function added              | 0     | Not found                                |
| other problems found               | 1     | more solid validation about airport code |
| suggestions or additional function | 1     | further suggestions are given            |

2)  Second run of bad prompt

> <img src="./media/image30.png" alt="Evidence screenshot 30" />
>
> <img src="./media/image31.png" alt="Evidence screenshot 31" />
>
> <img src="./media/image32.png" alt="Evidence screenshot 32" />

| **Checklist item**                 | Score | Reason                                   |
|------------------------------------|-------|------------------------------------------|
| show in artifacts                  | 0     | just simple text, no artifacts           |
| record management                  | 1     | found save problem and give suggestions  |
| time-zone defect                   | 1     | detect timezone bug                      |
| multi-flight function              | 0     | Not found                                |
| import function                    | 0     | Not found                                |
| other problems found               | 1     | more solid validation about airport code |
| suggestions or additional function | 1     | further suggestions are given            |

3)  Third run of bad prompt

> <img src="./media/image33.png" alt="Evidence screenshot 33" />
>
> <img src="./media/image34.png" alt="Evidence screenshot 34" />
>
> <img src="./media/image35.png" alt="Evidence screenshot 35" />

| **Checklist item**                 | Score | Reason                                   |
|------------------------------------|-------|------------------------------------------|
| show in artifacts                  | 0     | just simple text, no artifacts           |
| record management                  | 1     | found save problem and give suggestions  |
| time-zone defect                   | 1     | detect timezone bug                      |
| multi-flight function              | 0     | Not found                                |
| import function                    | 0     | Not found                                |
| other problems found               | 1     | more solid validation about airport code |
| suggestions or additional function | 1     | further suggestions are given            |

4)  First run of better prompt

> <img src="./media/image36.png" alt="Evidence screenshot 36" /> <img src="./media/image37.png" alt="Evidence screenshot 37" /> <img src="./media/image38.png" alt="Evidence screenshot 38" />
>
> <img src="./media/image39.png" alt="Evidence screenshot 39" />
>
> <img src="./media/image40.png" alt="Evidence screenshot 40" />
>
> <img src="./media/image41.png" alt="Evidence screenshot 41" />
>
> <img src="./media/image42.png" alt="Evidence screenshot 42" />
>
> <img src="./media/image43.png" alt="Evidence screenshot 43" />

| **Checklist item**                 | Score | Reason                        |
|------------------------------------|-------|-------------------------------|
| show in artifacts                  | 1     |                               |
| record management                  | 1     |                               |
| time-zone defect                   | 1     |                               |
| multi-flight function              | 1     |                               |
| import function                    | 1     |                               |
| other problems found               | 1     |                               |
| suggestions or additional function | 1     | further suggestions are given |

5)  Second run of better prompt

> <img src="./media/image44.png" alt="Evidence screenshot 44" />
>
> <img src="./media/image45.png" alt="Evidence screenshot 45" />
>
> <img src="./media/image46.png" alt="Evidence screenshot 46" />
>
> <img src="./media/image47.png" alt="Evidence screenshot 47" />
>
> <img src="./media/image48.png" alt="Evidence screenshot 48" />

| **Checklist item**                 | Score | Reason                        |
|------------------------------------|-------|-------------------------------|
| show in artifacts                  | 1     |                               |
| record management                  | 1     |                               |
| time-zone defect                   | 1     |                               |
| multi-flight function              | 1     |                               |
| import function                    | 1     |                               |
| other problems found               | 1     |                               |
| suggestions or additional function | 1     | further suggestions are given |

7)  Third run of better prompt

> <img src="./media/image49.png" alt="Evidence screenshot 49" />
>
> <img src="./media/image50.png" alt="Evidence screenshot 50" /><img src="./media/image51.png" alt="Evidence screenshot 51" /><img src="./media/image52.png" alt="Evidence screenshot 52" />
>
> <img src="./media/image53.png" alt="Evidence screenshot 53" />
>
> <img src="./media/image53.png" alt="Evidence screenshot 53" />

| **Checklist item**                 | Score | Reason                        |
|------------------------------------|-------|-------------------------------|
| show in artifacts                  | 1     |                               |
| record management                  | 1     |                               |
| time-zone defect                   | 1     |                               |
| multi-flight function              | 1     |                               |
| import function                    | 1     |                               |
| other problems found               | 1     |                               |
| suggestions or additional function | 1     | further suggestions are given |

5.  Error analysis

I expected Claude to show the revised UI in Artifacts so I could directly inspect whether the suggested fixes were implemented. However, none of the bad-prompt runs created or displayed an updated component in Artifacts.

**Failure category:** **Missing task.**

In better prompt, I specify Fix the listed defects and improve if you can by apply artifacts, then all better prompts implement fix version in artifacts.

6.  Verdict

| **Prompt** | **Run 1** | **Run 2** | **Run 3** | **Average** |
|------------|-----------|-----------|-----------|-------------|
| Bad        | 4/7       | 4/7       | 4/7       | 4/7         |
| Better     | 7/7       | 7/7       | 7/7       | 7/7         |

The better prompt was clearly better than the bad prompt. The bad prompt scored 4/7 in all three runs, while the better prompt scored 7/7 in all three runs. My prediction for the bad prompt’s overall score was correct, but the specific results were slightly different from what I expected. I expected the bad prompt to show the improved version in Artifacts, but none of the runs did. However, all three bad-prompt runs identified the time-zone issue, which I did not expect them to find consistently.

## 3. Myth Test

The technique I choose is **"Double-check your answer."**

Prompt:

Create a UI component that allows a user to enter and save flight information. The form must include: Departure city, Departure airport, Departure terminal, Destination city, Destination airport, Arrival terminal, Flight number, Seats, Departure date and time, Arrival date and time.

The UI should have clear label and easy input fields, a save button, all fields except seats are required, validating date time based on arrival date time cannot be less then depart time, validating that departure city is not as same as destination city.

There is a saving button, after I click the button, show a clear error message if validation fails,

there is a section displays the generated JSON, the JSON structure is:

{

"departureCity": "San Francisco",

"departureAirport": "SFO",

"departureTerminal": "Terminal 1",

"destinationCity": "Dallas",

"destinationAirport": "DFW",

"arrivalTerminal": "Terminal 1",

"flightNumber": " F9 4000",

"seats": "25E",

"departureDateTime": "2026-06-17T12:32",

"arrivalDateTime": "2026-06-17T06:10"

}

Double-check your answer.

First turn

<img src="./media/image54.png" alt="Evidence screenshot 54" />

<img src="./media/image55.png" alt="Evidence screenshot 55" />

| **Checklist item**            | Score | Reason                                                            |
|-------------------------------|-------|-------------------------------------------------------------------|
| Required field                | 1     | Have everything I wanted                                          |
| Validation                    | 1     | Has validation                                                    |
| Date time validation          | 1     | Has validation of arrival time cannot earlier then departure time |
| Departure – destination check | 1     | Has validation of departure and destination city are not same     |
| Readable format               | 1     | format is readable, clear, easily input                           |
| Output JSON format            | 1     | result JSON is valid                                              |

Last statement is import: One more thing to consider: these are local times with no time zone. On some real westbound flights, the local arrival time is earlier than the local departure time, and this rule would block them. If that matters for you, I can add time-zone fields and compare the actual moments in time.

Second Run

<img src="./media/image56.png" alt="Evidence screenshot 56" />

<img src="./media/image57.png" alt="Evidence screenshot 57" />

| **Checklist item**            | Score | Reason                                                            |
|-------------------------------|-------|-------------------------------------------------------------------|
| Required field                | 1     | Have everything I wanted                                          |
| Validation                    | 1     | Has validation                                                    |
| Date time validation          | 1     | Has validation of arrival time cannot earlier then departure time |
| Departure – destination check | 1     | Has validation of departure and destination city are not same     |
| Readable format               | 1     | format is readable, clear, easily input                           |
| Output JSON format            | 1     | result JSON is valid                                              |

There is a double-checked session that have some defect detected. Such as Equal times are allowed. Time zones aren't considered.

Third run

<img src="./media/image58.png" alt="Evidence screenshot 58" />

<img src="./media/image59.png" alt="Evidence screenshot 59" />

<img src="./media/image60.png" alt="Evidence screenshot 60" />

| **Checklist item**            | Score | Reason                                                            |
|-------------------------------|-------|-------------------------------------------------------------------|
| Required field                | 1     | Have everything I wanted                                          |
| Validation                    | 1     | Has validation                                                    |
| Date time validation          | 1     | Has validation of arrival time cannot earlier then departure time |
| Departure – destination check | 1     | Has validation of departure and destination city are not same     |
| Readable format               | 1     | format is readable, clear, easily input                           |
| Output JSON format            | 1     | result JSON is valid                                              |

There is a session **What I checked**, I think this is work by Double-check your answer. And **Assumptions I made** part is also extra.

Conclusion:

| **Prompt** | **Run 1** | **Run 2** | **Run 3** | **Average** |
|------------|-----------|-----------|-----------|-------------|
| Bad        | 6/6       | 6/6       | 6/6       | 6/6         |
| Better     | 6/6       | 6/6       | 6/6       | 6/6         |

This result shows a limitation of the checklist I created at the beginning. The checklist only measured whether the required UI features were implemented, so these extra checks and observations did not increase the score.

It added sections such as

- There are two problems with your sample JSON

- What I double-checked

- What I checked

- Assumptions I made

which did not appear in the original version. I think these extra sections were made by the double-check instruction. Meanwhile, it produced assumptions that doubt the correctness of my command. It did produce a meaningful qualitative difference. It encouraged additional self-checking and surfaced extra considerations.

## 4. Reflection

In a prompt, elements such as **context, task, format, constraints, and examples** are all important for producing reliable results. My usual prompts are often too simple. I may provide only a small amount of context and a vague task while leaving out format, constraints, or examples. This often causes the output to be different from what I actually want.

One thing that stood out to me was the bad prompt in **2.3 Critique Prompt to Improve UI Component**. Because I did not explicitly ask Claude to use Artifacts, none of the three bad-prompt runs created an updated component in Artifacts. This showed me that I should clearly state what I expect instead of assuming the LLM already understands my intention.

The same problem appeared in **2.2 Extract**. When I did not specify the JSON structure, the output contained too much irrelevant information and became difficult to use directly. In the better prompt, I provided the exact JSON format and constraints, and the results became much cleaner and more useful.

Clear requirements also mattered in **2.1 Generating a UI Component**. In the bad prompt, I only asked for “date and time,” and several runs created only departure date and time. In the better prompt, I explicitly asked for both departure and arrival date and time, and Claude followed the requirement correctly.

What surprised me most was how the LLM makes assumptions when the prompt does not fully specify something, and how certain phrases can make it question those assumptions. Adding **“Double-check your answer”** did not improve the checklist score, but Claude added sections such as **“What I checked”** and **“Assumptions I made.”** It also noticed the time-zone issue, which I had not included in my checklist. This showed me that leaving some room for the model to review the task can be useful. However, extra assumptions may also be wrong, so they still need to be reviewed carefully.

## 5. Personal Prompt Template

### Context

Describe the background of the task and explain why the result is needed.

### Task

Clearly describe what needs to be done. Break complex tasks into specific actions.

- [ ]

- [ ]

- [ ]

### Format

Clearly define the expected input/output format.

Input JSON

```json

{

"": "",

}

```

Output JSON

```json

{

"": "",

}

```

### Constraints

List all important rules and limitations.

- [ ]

- [ ]

- [ ]

### Example

Provide an example when the expected result may be difficult to understand.

### Self-check and Assumptions

Identify assumptions or ask LLM to give assumptions or suggestions.
