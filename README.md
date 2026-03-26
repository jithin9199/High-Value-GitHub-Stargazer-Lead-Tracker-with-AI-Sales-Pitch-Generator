1. Schedule Trigger – Polling for New Stargazers

This is where everything begins. The workflow runs automatically every 5 minutes, so you don’t have to start it manually. Think of it like a heartbeat that keeps checking for updates in the background. You can always adjust the timing depending on how frequently you want new data.

2. HTTP Request – Fetch Stargazers

Once triggered, the workflow calls the GitHub API to get a list of people who starred the repository. This returns basic information about each user, like their username, profile link, and avatar.

Since GitHub doesn’t send notifications for new stars, this step is necessary to actively fetch the data.

3. Split Out – Process Each User Individually

The API gives a list of users in one bundle. This step breaks that list into separate items so each user can be handled one by one.

This makes the workflow more flexible and allows us to process multiple users efficiently instead of treating them as a single group.

4. HTTP Request – Fetch Detailed Profile

After splitting, the workflow fetches full details for each user. This includes useful information like their bio, company, number of followers, repositories, and more.

This step is important because the initial data is limited, and we need deeper insights to identify valuable users.

5. Filter – Identify High-Value Leads

Not every user is worth reaching out to. This step filters out less relevant profiles and keeps only users who meet certain criteria.

For example:

Users with more than 100 followers
OR users with more than 50 public repositories

This helps focus only on influential or active developers and avoids unnecessary noise.

6. AI Agent – Smart Analysis

This is the “brain” of the workflow. It takes the user’s profile information and prepares it for analysis.

The AI is given clear instructions to generate a short, compelling reason why this person is worth contacting. This ensures consistent and meaningful output.

7. OpenAI Model – Generate Sales Pitch

Here, the actual AI model creates a personalized one-line pitch based on the user’s profile.

Instead of generic messages, it produces something tailored, like:
“Reach out to this open-source contributor who is actively building and engaging with the developer community.”

This makes outreach more effective and professional.

8. Send to Slack – Notify the Team

Finally, all the useful information is sent directly to your Slack channel.

The message includes:

Name and username
Profile link
Followers and repository count
Company and bio
AI-generated pitch
