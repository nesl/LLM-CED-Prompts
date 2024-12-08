# Prompts for Detecting Complex Event 3
## Zero-shot
```
Imagine you are given a sequence of activities as live streaming.
At each window, you get the current activity label, and your goal is to output a timely detection of whether, at the current time, a specific type of event happens.
Each activity label is sampled every 5 seconds, so you can think of each label as the activity that happens during this 5-second time window.
To help you better understand the problem, I give you an example input below, which is a live-streaming list of activities:
['walk', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'flush_toilet', 'flush_toilet', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk']

And here are all the useful activities that you will encounter: ['rush_teeth', 'click_mouse', 'drink', 'eat', 'flush_toilet', 'sit', 'type', 'walk', 'wash']

Now, we are interested in the complex event “inadequate brushing time”, which is defined as:
“Brushing teeth for less than 2 minutes. If brushing stops, wait for 10 seconds. If the person continues brushing after 10 seconds, then continue the counting; otherwise, report a violation immediately and reset the system.”
The event label for this complex event is 3.

Please mimic a real-time detector that can output the corresponding event label when you discover the event takes place; otherwise, 0.
That said, your output sequence should be the same length as the input activity sequence.

Now consider this example:

Input: $AE_SEQUENCE$

# Think step by step, and do not write codes. Your answer should follow this format, using plain text without any formatting:
Output: []
```
To use the prompt above, replace `$AE_SEQUENCE$` with a sequence of activity labels. For example, try with

```['sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'walk', 'walk', 'walk', 'walk', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'wash', 'brush_teeth', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'walk', 'walk']```

The output should be:
```[0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 3, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]```

## Few-shot (k=3)
```
Imagine you are given a sequence of activities as live streaming.
At each window, you get the current activity label, and your goal is to output a timely detection of whether, at the current time, a specific type of event happens.
Each activity label is sampled every 5 seconds, so you can think of each label as the activity that happens during this 5-second time window.
To help you better understand the problem, I give you an example input below, which is a live-streaming list of activities:
['walk', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'flush_toilet', 'flush_toilet', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk']

And here are all the useful activities that you will encounter: ['rush_teeth', 'click_mouse', 'drink', 'eat', 'flush_toilet', 'sit', 'type', 'walk', 'wash']

Now, we are interested in the complex event “inadequate brushing time”, which is defined as:
“Brushing teeth for less than 2 minutes. If brushing stops, wait for 10 seconds. If the person continues brushing after 10 seconds, then continue the counting; otherwise, report a violation immediately and reset the system.”
The event label for this complex event is 3.

Please mimic a real-time detector that can output the corresponding event label when you discover the event takes place; otherwise, 0.
That said, your output sequence should be the same length as the input activity sequence.

Example 1:
Input: ['sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'walk', 'walk', 'walk', 'walk', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'wash', 'brush_teeth', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'walk', 'walk']
Output: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

Example 2:
Input: ['sit', 'sit', 'sit', 'sit', 'walk', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk']
Output: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 3, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

Example 3:
Input: ['sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk']
Output: [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 3, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]

Now consider this new data:

Input: $AE_SEQUENCE$

# Think step by step, and do not write codes. Your answer should follow this format, using plain text without any formatting:
Output: []
```
To use the prompt above, replace `$AE_SEQUENCE$` with a sequence of activity labels.
