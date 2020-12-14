# About The Project

Imagine having a new musical instrument from your phone that encourages movement, different dance moves, and a love for experimentation. Our project idea aims to fill this potential hole in people’s lives by taking accelerometer data from a smartphone and manipulating these incoming signals to produce vibrant, unique music relative to the person's movement.

# Why Create Music from Movement?

For people who are indoors most or all of the day (either working at home or isolating), one might have heard of the term 'Quarantine Fatigue'. Quarantine fatigue is caused by a reduction in physical activity which affects one's mind \[[1](/Movement-Synthesizer/references)\]. According to the American Heart Association even small bursts of movement are beneficial to one’s health \[[2](/Movement-Synthesizer/references)\]. By having the collection of the information be tied to a smartphone, it allows flexibility on the user’s behalf. End users can collect the data while running, walking, or even standing. To encourage movement, the longer someone moves, the longer the song will be!

In addition, even if the music isn’t a Mozart worthy masterpiece, having a low level of background music can help boost creativity in one’s endeavors \[[3](/Movement-Synthesizer/references)\]. According to the Harvard Medical School, “music can enhance the function of neural networks, slow the heart rate, lower blood pressure, and reduce levels of stress hormones, appealing to end users who might be stressed due to their environment or other factors \[[4](/Movement-Synthesizer/references)\]. 

Inspired by the benefits of both these exercises, our project combines them into an easily accessible smartphone program targetted towards people who are spending more time than usual indoors and sitting down (e.g. students, remote workers).

# How it Works

The Movement-Synthesizer captures motion from the x, y, and z coordinates of smartphone accelerometer data. In return, it translates signals from those three axes into individual frequencies audible to the human ear that sound like tuned music chords. This process involves some signal amplifying, frequency 'tuning', and filtering; a more in-depth coverage of the calculations to produce the final product can be found under the 'Explaing the Black Box' section. 

For the purpose of making specific music chords that sound 'pleasing' to the human ear, the x axis has been set up to be the 'base' or the 'root' note. The y and z axes are tuned accordingly to the 'root' note and a randomly selected chord. This produces chords that sound 'pleasing' to the human ear, like partial major or minor chords, but also allows for some flexibility in pitch for the y and z axes (more information is covered in the 'black box' section below!). Regardless, an increase in acceleration in any axis will result in an increase in frequency in the respective axis of movement. In music terms, this will increase the pitch of the notes being played. Likewise, a decrease in acceleration will result in a decrease in frequency in the respective axes of movement. To add variance to the pitch of the chords, the user should move frequently and move around in all three directions of motion.

We looked at three primary movements to encourage users to move their body as much as they can: shuffling (side-to-side), bumping (front-back), and jumping (up-down).

- TODO include videos of movement, like in Dad Dancing website

- Talk about motion model 
- Talk about sensors 

## Methods in Detail: Explaining "The Black Box"
There are four distinct methods that we used to process our input to reach our output. We will walk through them step-by-step to ensure transparency:
### Fourier Analysis 

### Pitch Tuning Algorithm 

### Chord Selection 

The chord selection is randomized so that the generated music does not sound repetitive. This design decision was made only after experimenting with the chord selection being attached to other variables such as the note of the y axis or z axis; we found that when there was little movement around either axis the generated music played the same three notes repeatedly. 

It selects between four chords: a major chord, a minor chord, a minor chord from the perfect 4th of the base note, and a major chord from the perfect 4th of the base note. After its selection, it will return a vector of three integers to add to the starting index of the selection of piano note frequencies. These three integers correspond to the notes needed to produce the selected chord in a modulo 12 Western music system. 

Here is what each chord sounds like with a concert A4 (440 Hz): 
- Major chord: 
<audio controls src="/media/cc0-audio/t-rex-roar.mp3"></audio>
- Minor chord:
<audio controls src="/media/cc0-audio/t-rex-roar.mp3"></audio>
- Minor chord from the perfect 4th interval (inverted such that the base note remains the lowest frequency): 
<audio controls src="/media/cc0-audio/t-rex-roar.mp3"></audio>
- Major chord from the perfect 4th interval (inverted such that the base note remains the lowest frequency): 
<audio controls src="/media/cc0-audio/t-rex-roar.mp3"></audio>

The reason why the model is limited to these four chords is because other chords (augmented chords, devil's triad) sounded objectively painful when tested on two human ears. Since it is hard to quantify what sounds 'good' or 'bad' with a sample size of two people, our group found research conducted by Pennsylvania State University that showed the majority of people prefer chords that are found in the harmonic series of the base note \[[5]\](https://sites.psu.edu/siowfa15/2015/09/16/what-makes-chords-sound-good/)

Note that the perfect 4th is a misleading yet common term in music theory as it is technically 2.5 'whole tones' above the base frequency. Since 12-tone music (Western music) is a modulo 12 arithmetic system based on 'half tones', perfect 4ths are represented as 5 'half tones'. 

### Playing Back the Music 


## Example: Tiktok Dance Ale's Sister Did

- Add graphs, add video of movement

This dance involves a lot of movement around all three axes. Notably, however, there are repeated movements in _ directions. There are notable variations in pitch in these directions with a slight variation in pitch in the other direction because of this pattern of movement. You can listen to the music generated below!


# References
Our references are listed [here](https://caitlincoffey.github.io/Movement-Synthesizer/references). This is not mentioned in our references, but we would like to thank the QEA teaching team for their help and support throughout this project!

<!--- Thoughts from the lecture:
- Do MLA citations and have perhaps a separate references page. 
- [1] inline citations, whenever you're taking information from a reference you should use it. Note that inline citations should be at the end of the sentence, like this [1].
- How to make equations: [stackoverflow](https://stackoverflow.com/questions/26275645/how-to-support-latex-in-github-pages)
- For graphs, choose distinguishing colors, different line thicknesses.
- https://docs.google.com/presentation/d/1ZrCd_3JE7x1tYL_IcSek4cTsEc63TjfPzzRDT7T8hRs/edit#slide=id.gb06d338265_0_42
Value Creation
The proof-of-concept supports a specific user group(s) in clearly defined ways. The connection between the proof-of-concept and the user group is clear, and based on existing research and/or a strong understanding of particular areas of opportunity.
This criterion is linked to a Learning Outcome Motion Model
Your motion model should demonstrated a clear understanding of the dynamics of your motion, the degrees of freedom and their time derivatives, and the important frequencies. You should explain how your model informed your data collection, and what, if any, modifications were made to the model following experimentation.
This criterion is linked to a Learning Outcome Proof-of-Concept
The proof-of-concept should include a selection of sensors that are appropriate for the specific application. The experiment(s) should demonstrate some aspect of how the product would work in reality. Next steps for the proof-of-concept (e.g. additional experiments, changes to the design) should be well articulated.
This criterion is linked to a Learning Outcome Algorithm Development
The algorithm(s) for data analysis should demonstrate a clear understanding of Fourier analysis, frequency and time domains, and motion model dynamics. The project website should clearly explain the application of the algorithm to the experimental data through the use of appropriate equations and graphics.
This criterion is linked to a Learning Outcome Overall Presentation and Delivery of Information
The website is professional and well-organized. The information is clear, easy to understand, and appropriate for the intended audience.
--->