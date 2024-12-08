# Prompts for Detecting Complex Event 2 
## Zero-shot
```
Imagine you are given a sequence of activities as live streaming.
At each window, you get the current activity label, and your goal is to output a timely detection of whether, at the current time, a specific type of event happens.
Each activity label is sampled every 5 seconds, so you can think of each label as the activity that happens during this 5-second time window.
To help you better understand the problem, I give you an example input below, which is a live-streaming list of activities:
['walk', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'flush_toilet', 'flush_toilet', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk']

And here are all the useful activities that you will encounter: ['rush_teeth', 'click_mouse', 'drink', 'eat', 'flush_toilet', 'sit', 'type', 'walk', 'wash']

Now, we are interested in the complex event “sanitary eating habit violation”, which is defined as:
“No wash hands at most 2 minutes before having a meal (including eat and drink). The hand washing should at least last for 20 seconds consecutively, and if they touch other things (including brush, click, flush and type) after washing hands and before having meals, they need to wash hands again. For each violation, we only trigger alert at the beginning of each meal session to avoid redundancy. Eat, drink, and sit will not interrupt each meal session, while other activities will.”
The event label for this complex event is 2.

Please mimic a real-time detector that can output the corresponding event label when you discover the event takes place; otherwise, 0.
That said, your output sequence should be the same length as the input activity sequence.

Now consider this example:

Input: $AE_SEQUENCE$

# Think step by step, and do not write codes. Your answer should follow this format, using plain text without any formatting:
Output: []
```
To use the prompt above, replace `$AE_SEQUENCE$` with a sequence of activity labels. For example, try with

```['wash', 'wash', 'walk', 'sit', 'sit', 'sit', 'flush_toilet', 'sit', 'sit', 'sit', 'sit', 'eat', 'eat', 'eat', 'sit', 'sit', 'sit', 'sit', 'eat', 'eat', 'sit', 'sit', 'eat', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk']```

The output should be:

```[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 2, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]```

## Few-shot (k=3)
```
Imagine you are given a sequence of activities as live streaming.
At each window, you get the current activity label, and your goal is to output a timely detection of whether, at the current time, a specific type of event happens.
Each activity label is sampled every 5 seconds, so you can think of each label as the activity that happens during this 5-second time window.
To help you better understand the problem, I give you an example input below, which is a live-streaming list of activities:
['walk', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'flush_toilet', 'flush_toilet', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk']

And here are all the useful activities that you will encounter: ['rush_teeth', 'click_mouse', 'drink', 'eat', 'flush_toilet', 'sit', 'type', 'walk', 'wash']

Now, we are interested in the complex event “sanitary eating habit violation”, which is defined as:
“No wash hands at most 2 minutes before having a meal (including eat and drink). The hand washing should at least last for 20 seconds consecutively, and if they touch other things (including brush, click, flush and type) after washing hands and before having meals, they need to wash hands again. For each violation, we only trigger alert at the beginning of each meal session to avoid redundancy. Eat, drink, and sit will not interrupt each meal session, while other activities will.”
The event label for this complex event is 2.

Please mimic a real-time detector that can output the corresponding event label when you discover the event takes place; otherwise, 0.
That said, your output sequence should be the same length as the input activity sequence.

Example 1:
Input: ['wash', 'wash', 'walk', 'sit', 'sit', 'sit', 'flush_toilet', 'sit', 'sit', 'sit', 'sit', 'eat', 'eat', 'eat', 'sit', 'sit', 'sit', 'sit', 'eat', 'eat', 'sit', 'sit', 'eat', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk']
Output: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 2, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

Example 2:
Input: ['wash', 'wash', 'wash', 'wash', 'walk', 'walk', 'walk', 'walk', 'sit', 'sit', 'sit', 'sit', 'drink', 'sit', 'eat', 'eat', 'sit', 'sit', 'eat', 'eat', 'eat', 'walk', 'walk', 'walk', 'walk', 'sit', 'eat', 'eat', 'eat', 'drink', 'drink', 'drink', 'eat', 'eat', 'eat', 'eat', 'eat', 'eat', 'sit', 'sit', 'sit', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk']
Output: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

Example 3:
Input: ['wash', 'wash', 'wash', 'wash', 'walk', 'walk', 'sit', 'sit', 'sit', 'flush_toilet', 'wash', 'wash', 'wash', 'sit', 'eat', 'eat', 'drink', 'sit', 'sit', 'drink', 'drink', 'drink', 'drink', 'drink', 'drink', 'eat', 'eat', 'eat', 'wash', 'wash', 'wash', 'wash', 'wash', 'sit', 'drink', 'drink', 'eat', 'eat', 'sit', 'sit', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk']
Output: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 2, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

Now consider this new data:

Input: $AE_SEQUENCE$

# Think step by step, and do not write codes. Your answer should follow this format, using plain text without any formatting:
Output: []
```
To use the prompt above, replace `$AE_SEQUENCE$` with a sequence of activity labels.
