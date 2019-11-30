# FAB
 A dummy’s program for self-paced forward and backward reading.

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
 
FAB is designed to run psychological or linguistic tasks that allow participants to go through sequential stimuli on their own paces, with reaction time recorded. The primary goal of FAB is to provide a free and handy instrument which simulate the eye-tracking process to explore the mechanism of human cognition. At the same time, the flexibility of FAB also enable it to carry other psychological experiments (e.g., Stroop, IAT, mental rotation, perceptual simulation, and stimuli display for developmental experiments).

Based on website web languages (JavaScript, HTML, and CSS), FAB does not require you to install any special software on your own computer or computers used to run the experiments. All you need is a common web browser (e.g., Chrome or Firefox is recommended). Both task generation and data collection run locally by default, so the Internet connection is not required. Reach out for any question: gongtiw@gmail.com

<p style="text-align:center;"><img src="https://tianweigong.github.io/source_for_other_website/fab/screenshot.gif" width="600"></p>

# FABdesign (set up a task)
For designing your self-paced reading task, please open `FABdesign.html` with the browser.

## Part 1: Create Your Parameter File
### Step1: The Stimuli Setting
> Please choose the type of stimuli.

Choose `picture` if you *only* use pictures in the experiments, otherwise choose the text. The difference between the two is that `text`  will trigger two extra divisions to adjust the text layout and the segmentation pattern.

> Please choose background color for your screen.

The default color is RGB 192,192,192.

> Please set a layout for your text stimuli (only for text stimuli option).

Adjust the color, font size, font styles for the text. The stimulus layout will be identical to the example layout here. **The font size depends on the screen resolution ratio and whether you zoom with the browser, so please make sure not to zoom the browser now and at least try on the lab computer once before collecting data** .

>Please choose how the stimuli should display.
Differences between two display patterns are shown in the picture. Usually we choose `Moving window` option for linguistic experiments.

<p style="text-align:center;"><img src="https://tianweigong.github.io/source_for_other_website/fab/movingwindow.png" width="600"></p>

>Please choose your segmentation rule (only for text stimuli option).

There are three ways to segment the stimuli sequences. You should choose here and then reform your stimulus list correspondingly later.
- **by space:** for languages that use space to separate words or picture stimuli. If you write sentence `nice to meet you.`, it will display as `nice`, `to`, `meet`, `you.`
- **by character:** for character-based languages. If you write sentence `很高兴认识你。`, it will display `很`, `高`, `兴`, `认`, `识`, `你。` The punctuations `。`, `，` , `、`, `？`, `！`, `：`, `；` will be displayed together with the last character rather than independently.
- **by '|', customized:** for other segmentation rule.

### Step 2: The Keyboard Setting

>Do you allow participants to go back during the learning process?

If you choose yes, participants will be able to go back-and-forth during the task, like an eye-tracking process. Data would be richer but also more complicated. If you choose no, participants can never look at the previous words/pictures once they press the forward key.

>Please press and save the response keys.

After considering the forward/backward response key, you can press it, check its information in the `key cube`(at lower right), and then click `save it as forward key` or `save it as backward key` to save it. If you want to make a change, you can press another key and click the button again. The keyboard information is compatible since different browsers use same key code, that is, you are confident to tell participants to press say "J " key, whenever they are using IOS or Windows, Safari or Chrome, etc. However, the physical positions might differ among keyboards.

### Step 3: Instruction

>Do you want a special layout for instruction?

If you choose `yes`, you can set up a special layout for instruction part. The instruction content will be designed in the CSV file together with your stimuli.

### Step 4: Comprehension Questions and Feedbacks

>Do you have any comprehension question for participants?

Choose `yes` if you have comprehension questions for some/all stimuli. The questions will be listed in the CSV file but here you can set up how participants answer those questions.

- **Yes, and they are multichoice questions:** for like yes/no questions. Four answer levels at most could be set up. The keyboard setting procedure is identical to forward/backward keys. Forward/backward keys chosen above are allowed to be also set up as answer responses. You can indicate the labels for different answers in the dataset. If you want to record accuracy or give feedback to participants, the answer labels set here should be identical to the labels in `fab_key` column in CSV (see details later).
- **Yes, and they are text-input questions:** for all more complex questions. Participants will see the question followed by a textarea input. Once finishing the answer, they can click the submit button to continue.
- **No:** if you choose this option, this step is finished. You do not need to indicate anything about the comprehension question in CSV as well.

>Do you want a special layout for comprehension questions?

You can set the special layout for comprehension questions, or the layout would be identical to stimuli's layout.

>The questions will appear __ ms later after the final windows disappear.

Usually the comprehension question should appear immediately after the end of the stimuli. However, the function here not only facilitate more complex linguistic experiment setting, but also enable many other psychological experiments. If you want to give different delays for different trials, you can set up an extra column `fab_qwait` in your CSV (see details later).

>Do you want to give the feedback to participants' answer?

You can give feedback to participants. **After receiving the feedback, participants need to press the forward key to continue (which should be indicated in the instruction)**. FAB will record the answer as correct only when it exactly matches the correct answer. Therefore, feedback for text-input answer is allowed but not recommended. The font and size of feedback will be the same as questions, and an italic style is added. The feedback color will be blue (RGB 0,0,255) for positive and red (RGB 255,0,0) for negative.

If you want to give feedback only for some special trials (for practical trials), you can choose `yes` here and then set up an extra column `fab_feedback` in CSV file (see details later).

### Step 5: The "End of Experiment" Message

Here you can input the message you want to show when participants finish the task. All other instructions or breaks could be set later in CSV file (see details later).

### Step 6: Download the Parameter File

Now you have finished the first part and can get the first “card” for FAB. 

- Click `saving the experimental parameter file` and an `exp.js` file will be saved in the default download folder of your browser. 
- Move `exp.js` to `jsfile` folder under  `FABrunning`.

**IMPORTANT:**The file name should be exact `exp.js`, not `exp(1).js`, `exp(2).js` or anything else. If so, please rename it as `exp.js`.

## Part 2: Create Your Stimulus File

### Step 1: Create and Check Your CSV File

Since almost all psycholinguistic researchers write their stimuli in spreadsheet software (e.g., Excel) firstly before conducting the experiment, FAB will just use the sheet to make stimulus file. Here is one example of valid stimulus list:

<p style="text-align:center;"><img src="https://tianweigong.github.io/source_for_other_website/fab/stimulidemo.jpg" width="600"></p>

- `fab_stimuli` *necessary*: Add `/` at the beginning and the end of the stimuli (You can do it instantly, check here). Add `*` to separate stimuli into different regions, then FAB will support region analysis. If you want to add a fixation `+` at the beginning of sentences, but don't want participants to go back to the fixation later (see the demo above), you can rewrite the sentence as `/+/The old lady lived further away from the city center./`. Namely, `/` can help separate stimuli into different loops, where participants can only go back-and-forth within the loop.

- `fab_question`: You can add one question for each stimulus, which could be displayed as texts or a picture. If you want to present multiple questions for one stimulus, add blank rows below that stimulus and only type in your second, third... questions.

- `fab_key`: The correct answer to comprehension questions. This column is necessary if you want the accuracy data or feedback presentation.

- `fab_feedback`: A column for customizing which trials to present to feedback. 

- `fab_instruction`: You can add picture (recommended) or text instruction *before* each stimulus. Participants will click a `next` button to continue. Scrolling is allowed so the content could be long.

- `fab_qwait`: A column for customizing the delay between stimuli and comprehension questions.

- `list`, `block`, `condition`: You can add other columns. The information will not be used in FAB but will appear in the dataset, which may benefit data analysis.

#### Notes for Your CSV File
All keywords starting with `fab_` are case-sensitive so make sure you give right names.

There is another important thing to check before export the CSV. Since CSV interpret the English comma as a default delimiter, we cannot include any English comma in the cells, or the delimiter process would go wrong. This sounds ridiculous for linguistic tasks but there is really an easy way to solve it. Just find all `,` and replace with `&#44`, a code for the English comma in HTML. Participants will see commas as usual in the experiment.

### Step 2: Compile Your CSV File

- Export the sheet as CSV in your spreadsheet software.
- Upload the CSV by click `Choose File`. 
- After uploading (choosing) CSV, you can get the `sti.js` file by click `save the experimental stimulus file`.
- Put `sti.js`  on `jsfile` folder under  `FABrunning`(just as `exp.js`).

## Step 3: Prepare Other Picture Files

If you indicate any pictures (jpg,bmp,png) in instruction or stimuli, please put them into the `media` folder under  under  `FABrunning`.

# FABrunning
For running your self-paced reading task, open `FABrunning.html` with the browser.

- enter the subject ID 
- FAB will record the time participants spend on each window.
- After the experiment, the data file `data_subjectID.csv` will be saved in the default download folder of your browser.

Tips:
- If you want to make it fullscreen, open the fullscreen mode according to your browser.
- Terminate and save the incomplete data: `Shift+q`

# FABanalysis
For cleaning data and generating eye-tracking like indices, open `FABanalysis.html` with the browser.

- Choose data files of all participants by click `Choose Files` at the top of the website. **The column names should be identical for all files.**
- Click the indices you want to generate.
- Input the reading-time threshold to remove outliers.
- Click `Save the data processing file` to save the dataset.

The definition of indices are similar to eye-tracking tasks. Here we use an example to describe them.

<p style="text-align:center;"><img src="https://tianweigong.github.io/source_for_other_website/fab/indexdemo.jpg" width="600"></p>

## Window-based Indices
- `Gazes` is defined as the single dwelling time in any given window. In this demo, we set the outlier as gazes below 80 ms or beyond 5000 ms. We firstly took a look at the indices in the window level. 
- `First pass time` refers to the first gaze on the window (e.g., 344 ms for “kids”, 1361 ms for “felt”). 
- `Rereading time` refers to the sum of the durations of second and later gazes on the window (e.g., 485+207 = 692 ms for “kids”, 1361+863 = 2224 ms for “felt”). 
- `Total reading time` refers to the sum of the durations of all gazes on the window (e.g., 344 + 485 + 207 = 1036 ms for “kids” and 1361+863 = 2224 ms for “felt”). Total reading time equals to the addition of first pass time and rereading time.

## Path-based Indices
- `Number of regression out` refers to how many times the comprehender go back to the previous window from the present window (e.g., 1 for “kids”, 1 for “felt”). In the second line of gaze sequences, the gazes of “showed”, “all”, “the” were outliers. Therefore, the regression path should be regarded as from “dances” to “kids” and from “kids” to “older”. Accordingly, the number of regression out was zero for “show”, “all”, “the”. 
- `Number of regression in` refers to how many times the comprehender go back in the present window from the later window (e.g., 1 for “kids”, 0 for “felt”). Similarly, the number of regression in “showed”, “all”, “the” was zero. 
- `Probability of regression out` refers to the quotient of the number of regression out and the total gaze numbers of the present window (e.g., 0.33 for “kids”, 0.5 for “felt”). 
- `Probability of regression in` refers to the quotient of the number of regression in and the total gaze numbers of the present window (e.g., 0.33 for “kids”, 0 for “felt”). Since comprehenders cannot regress out from the first window, or regress in to the final window, the number/probability of regression out for the first window and the number/probability of regression in for the final window are always zero.
- `Regression path duration` is also called “go-past” time, referring to the time from first fixating the window to first moving past the window to the right, including time spent in rereading earlier windows. For “felt” in the example sentence, the regression path duration was 1361+499+485+712+207+287+440+663+704+863 = 6221. Since the comprehender of this example moved directly forward after the first gaze for other windows, the regression path duration for other windows were equal to the first pass time. 
- `Selected regression path duration` was regression path duration detached from time spent in rereading earlier windows (1361+863= 2224 for “felt”, and first pass time for all other windows). Since the regression path does not exist for the first window, the regression path duration and selected regression path duration will always equal to the first pass time for the first window.

## Exploratory Measures
The previous measures were adopted from global eye-tracking measures. Besides, FAB also provides two exploratory measures. 
- `Number of gazes` refers to how many valid gazes there are for the present window (e.g., 3 for “kids”, 2 for “felt”). 
- `Mean gaze duration` refers to the average duration of all gazes in the present window, equal to the total reading time divided by the number of gazes (e.g., 1036/3=345 ms for “kids”, 2224/2= 1112 ms for “felt”).

## Area-level Indices
In order to conducted analysis on the area level, FAB would remove the gaze outliers and then merge all gazes by areas as showed in the figure. After that, FAB treats areas as windows and calculates all indices following the same ways mentioned above.

# Online Experiment
To be continued

# FAQ
## Why my `Fabrunning.html` crushes?
check the following things for debugging :bug:
- The separating notion for `fab_stimuli` is `/` not `\\`.
- Remember to remove English comma in CSV stimulus list (see [here](#notes-for-your-csv-file)).

## How to link the picture stimuli/instructions/questions to stimulus list?
- For instructions, you can input the picture name (e.g., `ins1.jpg`) in the cell directly.
- For stimuli, you can write in these way: `/ram.jpg goat.jpg beetle.jpg/` or `/There is a picture1.jpg in my room./` (and choose `by space` as segmentation in `FABdesign.html`)
- For questions, you can input the question name (e.g., `question1.jpg`) in the cell directly. If you want to combine words and pictures in your questions, you need to add HTML code, but that is easy, just write in this way: `Did you see this object in the previous sentence?<br><img src='media/picture1.jpg'>` (`<br>` is for line breaking).

## Could FAB randomize my trial order?
FAB does not have the function to randomize the presentation of your trial, for you might have constraints that the automatic procedure cannot satisfy (e.g., three trials from the same condition cannot be present continuously; there should not be continuous four "yes" answers for the comprehension questions). Therefore, the best way for you is to make different randomized stimulus lists yourself, and add one  `list` column to indicate that.

## Could FAB display multiple pages of instructions?
Yes. Just add one blank row, input things on `fab_instruction` cell, and leave other cell empty.