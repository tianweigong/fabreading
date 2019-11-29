# FAB
 A dummy’s program for self-paced forward and backward reading.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
 
FAB is designed to run psychological or linguistic tasks that allow participants to go through sequential stimuli on their own paces, with reaction time recorded. The primary goal of FAB is to provide a free and handy instrument which simulate the eye-tracking process to explore the mechanism of human cognition.

Based on website web languages (JavaScript, HTML, and CSS), FAB does not require you to install any special software on your own computer or computers used to run the experiments. All you need is a common web browser (e.g., Chrome or Firefox is recommended). Both task generation and data collection run locally by default, so the internet connection is not required.

## FABdesign (set up a task)
For designing your self-paced reading task, please open `FABdesign.html` with the browser.

### Part 1: Create Your Parameter File
#### Step1: The Stimuli Setting
> Please choose the type of stimuli.
Choose the “picture” option if you *only* use pictures in the experiments, otherwise choose the text. The difference between the two options is that “text”  will trigger two extra divisions to adjust the text layout and the segmentation pattern.
> Please choose background color for your screen.
The default color is RGB 192,192,192.
> Please set a layout for your text stimuli (only for text stimuli option).
Adjust the color, font size, font styles for the text. The stimulus layout will be identical to the example layout here. ** The font size depends on the screen resolution ratio and whether you zoom with the browser, so please make sure not to zoom the browser now and at least try on the lab computer once before collecting data** .
>Please choose how the stimuli should display.
Differences between two display patterns are shown in the picture. Usually we choose `sequentially` option for linguistic experiments.
>Please choose your segmentation rule (only for text stimuli option).
There are three ways to segment the stimuli sequences. You should choose here and then reform your stimulus list correspondingly later.
- **by space: ** for languages that use space to separate words or picture stimuli. If you write sentence “nice to meet you.”, it will display as “nice”, “to”, “meet”, “you.”
- **by character: ** for character-based languages. If you write sentence “很高兴认识你。”, it will display “很”, “高”, “兴”, “认”, “识”, “你。” The punctuations `。`, `，` , `、`, `？`, `！`, `：`, `；` will be displayed together with the last character rather than independently.
- **by '|', customized: ** for other segmentation rule.

#### Step 2: The Keyboard Setting
>Do you allow participants to go back during the learning process?
If you choose yes, participants will be able to go back-and-forth during the task, like an eye-tracking process. Data would be richer but also more complicated. If you choose no, participants can never look at the previous words/pictures once they press the forward key.
>Please press and save the response keys.
After considering the forward/backward response key, you can press it, check its information in the `key cube`(at lower right), and then click `save it as forward key` or `save it as backward key` to save it. If you want to make a change, you can press another key and click the button again. The keyboard information is compatible since different browsers use same key code, that is, you are confident to tell participants to press say “J” key, whenever they are using IOS or Windows, Safari or Chrome, etc. However, the physical positions might differ among keyboards.

#### Step 3: Instruction



## FABrunning
For running your self-paced reading task (online/offline).


## FABanalysis
For cleaning data and generating eye-tracking like indices.
