#### Skin, The Bark of Man
## A Solution to the Engineering Physics Robot Competition
## image of the robot

Hello everyone. Every year the Engineering Physics Department at UBC creates a Summer robotics competition where 15-16 student teams are tasked with creating autonomous robots to preform a series of tasks and complete a mission. This tear's competition was themed after Marvel's Avengers.

Thanos has reached his evil goal of making half of the universe’s population disappear, brutally saving civilization from self-destruction by overpopulation. But in another parallel universe, his good twin brother Meta-Thanos known as Methanos has built an army of robots to counter his evil sibling’s intentions. Methanos is now sending these robots back in time to each one of the parallel universes to secure the Infinity Stones and rescue the Avengers. Meanwhile Thanos is deploying his own robot army to destroy the Avengers and gather the Infinity Stones in all universes.

These gods have engaged you, Engineering Physics students, to build them robots to go back in time to perform this purpose. As Thanos and Methanos look the same, you’re not really sure what side you’re on so you’d better make your robot able to function for both. As observers of just one of these universes, you will watch with delight or horror as your robots take part in the ultimate struggle between good and evil, between robots with flawless mechanical precision and those of questionable rigidity.

## Image of the competition surface

Two robots are positioned at the starting points and turned on. for hte purpose of the competition, one is called Thanos nad the other is called Methanos. However these two robots have the same objectives. Each robot has to follow a line up the ramp. From there , each robot has two different types of objectives :
1. Retreat the Infinity Stones: Follow the black tapes to find intersections. From there, the robots must head to the post and pick up the infinity stone. The posts have the same circular base size with different heights. With this mission, the robot continues to follow the line back the its targetted gauntlet. There are six small and shallow holes on the gauntlet where the robot must drop the infinity stones. Robots could either drop the stones one at a time or they can pickup multiple stones and drop them at the same time at the end of the run. There are a total of 6 Infinity Stones and each one counts for 2 points if it is dropped in the gauntlet.
## image of infinity stone
## image of the posts
## image of hte gauntlet (maybe that machine vision version )

2. Save the Avengers: There are a number pluchies randomly placed around the track. The mission with the plushies is to detect them and to guide them toward the plushy droping zone. There are two dropping points , one for Methanos and one for Thanos. But how does each robot know where to drop them ? Well each of these dropping zones has a Infra Red beacon used to create two different frequencies. Depending on the role , the robot must choose which IR beacon it must follow adn must drop the plshies there. Every plushy successfully dropped the has 1 point only and there are a total of 5 different plushies. 
## image of plshies
## image of the IR beacon 

The important note to keep in mind is that every round of the competition is only **2 minutes long** . In addition, all of these robots must have some method of handling collisions because **for every restart, the team will have a -2 deduction from their overall score** . **Assisting the robot, like giving it a nudge or pushing the arm if it is stuck is allowd but will reduce any score from there on to 1/17 of the score**. It is important to keep in mind that the strategy here is imperative for this competition.

## Our Strategy
Our initial strategy , after some time of working out possible solutions and testing them out (A list of these ideas like position tracking with a laser mouse, having a complicated 3-axis claw, using buke chains ) we decided to go with the strategy of picking up two stones from the shortest middle posts, going back to the gauntlet and dropping them off and then possibly going for plushies. As we though about going for plushies, we decided to use a camera and a Raspberry Pi to detect and go after the plushies. Since we decided to use a camera, we had the bold and dangerous idea of using the Pi Camera for the line following task as well. This decision led to a take a very different route for our robot design since the traditional method for line following is to use QRD sensors. 

## Image of QRD sensors

Our general strategy ended up being one that depends on the reliabiility and accuracy of hte robot in addition to relying on the speed. We needed speed since our robot was going into the opponent's territory. Since any collision is difficult to deal with in the middle of the competition, we decided to be wuick so that our robot would be able to return the stones to the gauntlet in less than a minute. From there on , we would decide to run again and restart or to go for the plushies. This way would have a guaranteed 4 points and this would give us an advantage in the competition. In addition to this, we decided to focus on some mechanical design in order to simplify the controll of the robot. for example a half circle in the front of the robot for parcking it accuratly in front of the posts. **So, enought strategy talk ...** 

And so it began, our jurny towards the creation of **Skin, Bark of Man**. Why call it that ? Well because obviosuly **Skin is the Bark of Man**.

### Chassis and  Body Design
Well, first we needed to try out our idea of how the robot would look adn work. In addition, some of us working on software needed a prototype to tesk their code on.

## Image of our first design

Well, not much to work on. It was a very quick prototype created with a aluminum base ccreated with a waterjet cutter. We put slots in the middle so that we could position the components at different points on the chassis.
We decided to use large and while wheel in order to increase the grip and the speed of movement. So for this prototype, we used a toy car wheel since in addition to having grip, it has a natural suspension effect for the control of the robot. Our robot had two caster wheel in the front as well.
We put a webcam at the front of the robot and we used it for line following . the early versions of the code are in the github history. After about three days of testing we got it to work, kind of ...
## Image of the robot saladding

After this we move to our other chassis version 2

## Image of the 3D model of the robot 
## Image of the 1 d base

This chassis was designed to be sturdy. This chassis is one piece. That's right. One piece of aluminum was cut out using the waterjet cutter with holes and edge. Then this body was properly bent and different sides wereconnected to each other with fasteners, and nuts and bolts.While this is more difficult to build and connet , the benefit is the irgidity of the robot.Most teams chose to make their chassis out of hardboard with lase jet cutters. During  the testing process and the competition, robot often fell out of the platform and collided with objects and other robots. The benefit of our metallic chassis was that the collisions and the dropping didn't damage our robot significantly and this proved to be very helpfull during the competition.

A couple of things to keep in mind for whoever decides to use a metallic chassis:
1. Make sure that you electrical circuits do not touch the body. **Shorting circuits is BAD. like VERY BAD .**
2. Try to make the chassis in a way that the circuits and interior of the robot could be change easily.
3. Im not sure about this one -- If you are planning to use a robot that has two or three level and is tall, having the robot with too many nuts and bolts connection and too rigid would sometime reduce the control over the robot. 

As for the wheels, we made the wheel out of **(what I don't know )** with the same dimensions of the toy wheel. We also added layers of **I forgot its name** to add to the friction. The reason for changing the wheel was that ,believe it or not , we needed more friction !

## image of the wheel


### Software

In order to talk about the software, we need to talk about our processors. We were provided with free stm32 bluepills for the purpose of controlling the robot. These chips are small, cheap and lite and they can be programmed using **C and C++**. Every team was given a budget of 150 dollars





You can use the [editor on GitHub](https://github.com/valavakilian/RobotController/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/valavakilian/RobotController/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
