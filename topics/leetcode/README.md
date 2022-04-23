# Design Leetcode
Disecting LeetCode website and designing various features that it supports.

## Functional Requirements
- Get list of problems
- Code editor to edit code in multiple languages
- Run the code
- Submit the code
- Contest
   - How is the code evaluated with low latency
   - How are the scores calculated?
   - How is leaderboard updated?
   - What all data is stored?
- Tagging of questions and filtering based on tags
- Subscriptions: payment and management of access to permium content
- Discussions: general discussion, discussions integrated into the problem
- Performance statistics


## Non-functional Requirements
- Highly available
- Low latency
- Eventual consistency

# Features
- Run/Submit Code - [notes](submit-code.md), [whiteboard](submit-code.draw)
- Contest - [notes](contests.md), [whiteboard](contests.draw)