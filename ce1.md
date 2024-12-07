# Prompts for Detecting Complex Event 1 
~~~
Imagine you are given a sequence of activities as live streaming. At each window, you get the current activity label, and your goal is to output a timely detection of whether, at the current time, a specific type of event happens. Each activity label is sampled every 5 seconds, so you can think of each label as the activity that happens during this 5-second time window. To help you better understand the problem, I give you an example input below, which is a live-streaming list of activities:
['walk', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'flush_toilet', 'flush_toilet', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk']

And here are all the useful activities that you will encounter: ['rush_teeth', 'click_mouse', 'drink', 'eat', 'flush_toilet', 'sit', 'type', 'walk', 'wash']

Now, we are interested in the complex event “workspace sanitary protocol violation”, which is defined as: “A person starts working without washing hands for at least 20 seconds after they use the restroom. The hand washing should at least last for 20 seconds consecutively. Each time when a violation happens, trigger an alert immediately at that window and then reset the system.” The event label for this complex event is 1.

Please mimic a real-time detector that can output the corresponding event label when you discover the event takes place; otherwise, 0. That said, your output sequence should be the same length as the input activity sequence.

Now consider this example:

Input: ['sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'sit', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'brush_teeth', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'wash', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk', 'walk']

# Think step by step, and do not write codes. Your answer should follow this format:
Output: []
~~~
