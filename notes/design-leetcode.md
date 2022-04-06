# Design Leetcode
Disecting LeetCode website and designing various features that it supports.

[Whiteboard](../diagrams/design-leetcode.draw)

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


## APIs
1. ```interpret_solution```
```
POST: https://leetcode.com/problems/<problem_slug>/interpret_solution/

request payload
{
   "question_id":"1",
   "data_input":"[2,7,11,15]\n9",
   "lang":"python3",
   "typed_code":"class Solution:\n    def twoSum(self, nums: List[int], target: int) -> List[int]:\n        ",
   "judge_type":"small"
}

response payload
{
   "interpret_id":"runcode_1649038816.9318714_9EjisreNz8",
   "test_case":"[2,7,11,15]\n9"
}
```

2. ```check (for run)```
```
GET: https://leetcode.com/submissions/detail/<interpret_id>/check/

response payload (not yet executed)
{
   "state":"STARTED"
}

response payload (execution completed)
{
   "status_code":10,
   "lang":"python3",
   "run_success":true,
   "status_runtime":"70 ms",
   "memory":13844000,
   "code_answer":[
      "[1,0]"
   ],
   "code_output":[
      
   ],
   "elapsed_time":129,
   "task_finish_time":1649039519089,
   "expected_status_code":10,
   "expected_lang":"cpp",
   "expected_run_success":true,
   "expected_status_runtime":"3",
   "expected_memory":6236000,
   "expected_code_answer":[
      "[0,1]"
   ],
   "expected_code_output":[
      
   ],
   "expected_elapsed_time":17,
   "expected_task_finish_time":1649036636282,
   "correct_answer":true,
   "total_correct":null,
   "total_testcases":null,
   "runtime_percentile":null,
   "status_memory":"13.8 MB",
   "memory_percentile":null,
   "pretty_lang":"Python3",
   "submission_id":"runcode_1649039518.7401695_ABejAalh5F",
   "status_msg":"Accepted",
   "state":"SUCCESS"
}
```

3. ```submit```
```
POST: https://leetcode.com/problems/two-sum/submit/

request payload
{
   "question_id":"1",
   "lang":"python3",
   "typed_code":"\"\"\"\npattern: dict\ntime: O(n log n)\nspace: O(1)\n\"\"\"\n\nclass Solution:\n    def twoSum(self, nums: List[int], target: int) -> List[int]:\n        seen = {}\n        for i, num in enumerate(nums):\n            search_elem = target - num\n            if search_elem in seen:\n                return [i, seen[search_elem]]\n            seen[num] = i\n    "
}

response payload
{
   "submission_id":673356331
}
```



4. ```check (for submit)```
```
GET: https://leetcode.com/submissions/detail/<submission_id>/check/

response payload
{
  "status_code": 10,
  "lang": "python3",
  "run_success": true,
  "status_runtime": "71 ms",
  "memory": 15148000,
  "question_id": "1",
  "elapsed_time": 87,
  "compare_result": "111111111111111111111111111111111111111111111111111111111",
  "code_output": "",
  "std_output": "",
  "last_testcase": "",
  "expected_output": "",
  "task_finish_time": 1649039705395,
  "total_correct": 57,
  "total_testcases": 57,
  "runtime_percentile": 81.54299999999998,
  "status_memory": "15.1 MB",
  "memory_percentile": 51.48569999999999,
  "pretty_lang": "Python3",
  "submission_id": "673356331",
  "status_msg": "Accepted",
  "state": "SUCCESS"
}

```


## References
1. https://dzone.com/articles/patterns-for-microservices-sync-vs-async
2. https://matthewminer.com/2015/02/21/pattern-for-async-task-queue-results
3. https://davidwalsh.name/javascript-polling

### Questions
1. How does the code editor support multiple languages
Does it download all the code for code editor for all
languages on page load? Because I don't see a network 
call when I change the coding language.
2. 
