# FAB
 A dummy’s program for self-paced forward and backward reading.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
 
FAB is designed to run psychological or linguistic tasks that allow participants to go through sequential stimuli on their own paces, with reaction time recorded. The primary goal of FAB is to provide a free and handy instrument which simulate the eye-tracking process to explore the mechanism of human cognition. At the same time, the flexibility of FAB also enable it to carry other psychological experiments (e.g., Stroop, IAT, mental rotation, perceptual simulation, and stimuli display for developmental experiments).

Based on website web languages (JavaScript, HTML, and CSS), FAB does not require you to install any special software on your own computer or computers used to run the experiments. All you need is a common web browser (e.g., Chrome or Firefox is recommended). Both task generation and data collection run locally by default, so the internet connection is not required.

## FABdesign (set up a task)
For designing your self-paced reading task, please open `FABdesign.html` with the browser.

### Part 1: Create Your Parameter File
#### Step1: The Stimuli Setting
> Please choose the type of stimuli.

Choose `picture` if you *only* use pictures in the experiments, otherwise choose the text. The difference between the two is that `text`  will trigger two extra divisions to adjust the text layout and the segmentation pattern.

> Please choose background color for your screen.

The default color is RGB 192,192,192.

> Please set a layout for your text stimuli (only for text stimuli option).

Adjust the color, font size, font styles for the text. The stimulus layout will be identical to the example layout here. ** The font size depends on the screen resolution ratio and whether you zoom with the browser, so please make sure not to zoom the browser now and at least try on the lab computer once before collecting data** .

>Please choose how the stimuli should display.

Differences between two display patterns are shown in the picture. Usually we choose `sequentially` option for linguistic experiments.

>Please choose your segmentation rule (only for text stimuli option).

There are three ways to segment the stimuli sequences. You should choose here and then reform your stimulus list correspondingly later.
- **by space: ** for languages that use space to separate words or picture stimuli. If you write sentence `nice to meet you.`, it will display as `nice`, `to`, `meet`, `you.`
- **by character: ** for character-based languages. If you write sentence `很高兴认识你。`, it will display `很`, `高`, `兴`, `认`, `识`, `你。` The punctuations `。`, `，` , `、`, `？`, `！`, `：`, `；` will be displayed together with the last character rather than independently.
- **by '|', customized: ** for other segmentation rule.

#### Step 2: The Keyboard Setting

>Do you allow participants to go back during the learning process?

If you choose yes, participants will be able to go back-and-forth during the task, like an eye-tracking process. Data would be richer but also more complicated. If you choose no, participants can never look at the previous words/pictures once they press the forward key.

>Please press and save the response keys.

After considering the forward/backward response key, you can press it, check its information in the `key cube`(at lower right), and then click `save it as forward key` or `save it as backward key` to save it. If you want to make a change, you can press another key and click the button again. The keyboard information is compatible since different browsers use same key code, that is, you are confident to tell participants to press say "J " key, whenever they are using IOS or Windows, Safari or Chrome, etc. However, the physical positions might differ among keyboards.

#### Step 3: Instruction

>Do you want a special layout for instruction?

If you choose `yes`, you can set up a special layout for instruction part. The instruction content will be designed in the CSV file together with your stimuli.

#### Step 4: Comprehension Questions and Feedbacks

>Do you have any comprehension question for participants?

Choose `yes` if you have comprehension questions for some/all stimuli. The questions will be listed in the CSV file but here you can set up how participants answer those questions.

- **Yes, and they are multichoice questions: **for like yes/no questions. Four answer levels at most could be set up. The keyboard setting procedure is identical to forward/backward keys. Forward/backward keys chosen above are allowed to be also set up as answer responses. You can indicate the labels for different answers in the dataset. If you want to record accuracy or give feedback to participants, the answer labels set here should be identical to the labels in `fab_key` column in CSV (see details later).
- **Yes, and they are text-input questions: **for all more complex questions. Participants will see the question followed by a textarea input. Once finishing the answer, they can click the submit button to continue.
- **No: ** if you choose this option, this step is finished. You do not need to indicate anything about the comprehension question in CSV as well.

>Do you want a special layout for comprehension questions?

You can set the special layout for comprehension questions, or the layout would be identical to stimuli's layout.

>The questions will appear __ ms later after the final windows disappear.

Usually the comprehension question should appear immediately after the end of the stimuli. However, the function here not only facilitate more complex linguistic experiment setting, but also enable many other psychological experiments. If you want to give different delays for different trials, you can set up an extra column `fab_qwait` in your CSV (see details later).

>Do you want to give the feedback to participants' answer?

You can give feedback to participants. **After receiving the feedback, participants need to press the forward key to continue (which should be indicated in the instruction)**. FAB will record the answer as correct only when it exactly matches the correct answer. Therefore, feedback for text-input answer is allowed but not recommended. The font and size of feedback will be the same as questions, and an italic style is added. The feedback color will be blue (RGB 0,0,255) for positive and red (RGB 255,0,0) for negative.

If you want to give feedback only for some special trials (for practical trials), you can choose `yes` here and then set up an extra column `fab_feedback` in CSV file (see details later).

#### Step 5: The "End of Experiment" Message

Here you can input the message you want to show when participants finish the task. All other instructions or breaks could be set later in CSV file (see details later).

#### Step 6: Download the Parameter File

Now you have finished the first part and can get the first “card” for FAB. Click `saving the experimental parameter file` and an `exp.js` file will be saved in the default folder of your browser. **IMPORTANT: **Move `exp.js` to `jsfile` folder in  `FABrunning`. The file name should be exact `exp.js`, not `exp(1).js`, `exp(2).js` or anything else. If so, please rename it as `exp.js`.

### Part 2: Create Your Stimulus File

#### Step 1: Create and Check Your CSV File

Since almost all psycholinguistic researchers write their stimuli in Excel firstly before conducting the experiment, FAB will just use the sheet to make stimulus file. Here is one example of valid stimulus list:

- `fab_stimuli` (necessary): 
- `fab_instruction`:
- `fab_question`:
- `fab_key`:
- `fab_feedback`:
- `fab_qwait`:
- `list`,`block`,`condition`:

#### Step 2: Compile Your CSV File
To be continued.


## FABrunning
For running your self-paced reading task (online/offline).


## FABanalysis
For cleaning data and generating eye-tracking like indices.
