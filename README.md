# camel-profile-sample
A little Apache Camel example with Spring Boot we can use to profile JVM and find spots for improvements


We have found a few spots to optimize the camel-core source code for thread contention and something else.

You can use a profile tool such as YourKit which is excellent at identifying spots and visualizing what goes on in the JVM.

We have used it in the past to optimise stuff. However recently Luca asked about making Camel startup faster: https://issues.apache.org/jira/browse/CAMEL-11321

And although fast startup is not excatly the same as runtime performance then they are still related. A profile can help identify places for improvements.

I have pushed a sample project at
https://github.com/davsclaus/camel-profile-sample

You can then run this via 

    mvn spring-boot:run

And then attach YourKit profiler.

However if you use IDEA then you can start YourKit, then from YourKit you can choose Integrate with IDE ... and then chose IDEA and then say ok even if IDEA is also running.

In IDEA you should see a YourKit icon if you right-click on the SampleCamelApplication to run this application, then you can chose that to profile, and it run the app with profiler (as shown below).

![YourKit-1](img/yourkit-1.png?raw=true "YourKit-1")

You then switch to YourKit and you should start see data.
To check for thread contention, then select the "Monitor Usage" tab, and then click the gear button with the play icon "Start Monitor Profile" which then starts capture data.

![YourKit-2](img/yourkit-2.png?raw=true "YourKit-2")

You can also pre-configure YourKit to run in different mode. For example to run in _call counting_ mode, you can
change this in the run dialog. Mind that you should press `apply` button, and then run the application by
right clicking and chose profile, otherwise the profiler is not started as well. This allows YourKit to run
in the chosen mode from the beginning. You can change the mode while YourKit is running, but if you want to
capture details during startup then you need to do as shown in the screenshot below:

![YourKit-3](img/yourkit-3.png?raw=true "YourKit-3")


#### YourKit License

For YourKit you can request a trial license that works for 2 weeks.
 