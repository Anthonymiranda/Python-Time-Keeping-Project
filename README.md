<h1>Python Task Time Keeping School Program</h1>


<h2>Description</h2>
<b>The python code on this repository was for my first full python project. It was a task time keeping program. Since there are apps that actually do this, I never fully finish the program or updated it. This project was to showcase my python learning with something I was concerned at the time - time management and productivity optimization.
</b>
<br />
<br />

<br />

<h2>Languages Used</h2>

- <b>Python</b>

<h2>Utilities Used</h2>

- <b>Replit</b> 
<h2>PART 1: Defining Your Problem</h2>

<p>I am interested in productivity and being productive. While I have made systems, habits, and routines in my life to help me be productive, my wife usually struggles. I want to create a program that helps with tracking the time we use on different activities and gives us recorded outputs that we can use to optimize our life.</p>

<p>I want to write a program that the user can choose from a selection of activities to track, then track the time duration of that activity until the user inputs that they are done. Throughout the day, the user can track the duration of those activities (gaming, work, exercise, sleep, commute, study) and get a set of outputs recorded to a spreadsheet. Some of the outputs would be a daily duration for the activity and the percentage of the day used on this activity based on a 24 hrs. Each activity would be added and the total would be subtracted from 24 hrs to get an “idle” time output. The outputs for the avg duration of each activity, the date, the percentage of the day, and idle time would be recorded in a spreadsheet. The purpose of this program is as an activity tracker that I and my wife can use to optimize our day/week/month.</p>

<h2>PART 2: Working Through Specific Examples</h2>

Example scenario 1:<br>
The user opens the program and is prompted to input their current activity.<br>
The user types in "gaming" and hits enter.<br>
The program starts a timer for gaming and displays a message saying "Timer started."<br>
After playing games for 2 hours, the user decides to take a break and types in "done" to stop the timer.<br>
The program calculates the time spent gaming as 2 hours and displays a message saying "Gaming time logged: 2.00 hours".<br>
The program prompts the user to input their next activity.<br>
The user types in "study" and hits enter to start the timer for studying.<br>
The program displays a message saying "Timer started."<br>
The user spends 1 hour studying and types in "done" to stop the timer.<br>
The program calculates the time spent studying as 1 hour and displays a message saying "Study time logged: 1.00 hours".<br>
The program prompts the user to input their next activity, and the process continues until the user is finished for the day.<br>
Example scenario 2:<br>
The user opens the program and is prompted to input their current activity.<br>
The user types in "sleep" and hits enter.<br>
The program starts a timer for sleeping and displays a message saying "Timer started."<br>
The user goes to sleep for 8 hours and wakes up in the morning.<br>
The user types in "done" to stop the timer.<br>
The program calculates the time spent sleeping as 8 hours and displays a message saying "Sleep time logged: 8.00 hours".<br>
The program prompts the user to input their next activity for the day.<br>
Example scenario 3:<br>
The user opens the program and is prompted to input their current activity.<br>
The user types in "workout" and hits enter.<br>
The program starts a timer for working out and displays a message saying "Timer started."<br>
After working out for 1 hour, the user types in "done" to stop the timer.<br>
The program calculates the time spent working out as 1 hour and displays a message saying "Workout time logged: 1.00 hours".<br>
The program prompts the user to input their next activity.<br>
The user types in "commute" and hits enter.<br>
The program starts a timer for commuting and displays a message saying "Timer started."<br>
After commuting for 30 minutes, the user types in "done" to stop the timer.<br>
The program calculates the time spent commuting as 0.50 hours and displays a message saying "Commute time logged: 0.50 hours".<br>
The program prompts the user to input their next activity.<br>
The user types in "end" to indicate that they are finished tracking activities for the day.<br>
The program calculates the total time spent on all activities, as well as the percentage of total time spent on each activity.<br>
The program logs the data in an Excel spreadsheet and displays a summary of the outputs<br>

<h2>PART 3: Generalizing Into Pseudocode</h2>
Import necessary modules: datetime, Workbook and load_workbook from openpyxl<br>
Set the filename to 'activity_log.xlsx'<br>
Try to load the workbook with the file name, if not found, create a new workbook, remove the active sheet, and create a new sheet called 'Activity Log'<br>
Append the column headers 'Date', 'Gaming', 'Workout', 'Study', 'Commute', 'Sleep', 'Idle' to the worksheet<br>
Create a dictionary called activity_dict with the keys 'gaming', 'workout', 'study', 'commute', 'sleep' ‘work’, and set all values to 0<br>
Set start_time to None<br>
Start an infinite loop<br>
Prompt the user to input the activity they are doing<br>
Check if the input is a valid activity, if not, print an error message and continue to the next iteration of the loop<br>
If start_time is None, set start_time to the current date and time and print a message that the timer has started<br>
Otherwise, calculate the time duration as the difference between the current time and start_time, in hours, and add it to the corresponding value in activity_dict<br>
Set start_time to None and print a message indicating the time logged for the activity<br>
Prompt the user if they are done tracking the current activity. If the input is 'done', set start_time to None<br>
Prompt the user if they are done tracking activities for the day. If the input is 'end', break out of the infinite loop<br>
Calculate the total time by summing the values in activity_dict<br>
Calculate the percentage of time for each activity by dividing the value in activity_dict by the total time, and store in activity_percentages<br>
Calculate the idle time by subtracting the total time from 24<br>
Get the current date and store it in the variable date<br>
Append the date, the values in activity_dict, and the idle time to the worksheet<br>
Save the workbook with the filename<br>
Print a summary of the activity log for the current date, including the time and percentage for each activity, as well as the idle time<br>

<h2>PART 4: Testing Your Program</h2>
After running the program, I notice that it is not outputting the time of the recorded activity after inputting “done.” it just asks for the next activity and the next. It also doesn’t clearly state how to output the times, how to output anything. In the code, I know you can write “end” to output duration totals for the day and create the spreadsheet but the user does not.

Here is my initial code for the loop.

    while True:
    activity = input("What activity are you doing? (gaming/workout/study/commute/sleep) ")
    if activity.lower() not in activity_dict:
        print("Invalid activity. Please try again.")
        continue

    if start_time is None:
        start_time = datetime.datetime.now()
        print("Timer started.")
    else:
        end_time = datetime.datetime.now()
        time_duration = (end_time - start_time).total_seconds() / 3600.0
        activity_dict[activity.lower()] += time_duration
        start_time = None
        # If user inputs "end", break out of loop
        if input("Are you done tracking activities for today?").lower() == 'end':
            break

    # If user inputs "done", stop tracking the current activity
    if input("Type 'done' to stop tracking the current activity: ").lower() == 'done':
        start_time = None

And here it is running. It doesn’t ever state how to “end” to the user.
(image here)

This was a quick fix for line 20 of the code to change the string from “"What activity are you doing? (gaming/workout/study/commute/sleep) " 
to
"What are you doing? (gaming/study/workout/commute/sleep) or type done to finish: "

This gave me the following output when ran:
(image here)

This fixes the issue of letting the end user know how to finish but after feedback from my wife, it doesn’t tell you how long you spent on the activities after you mark “done” to stop tracking and activity. It simply asks you what activity you want to track next.

The changes I made was an addition to the time recording loop from line 25 to 33. The code before was:

    if start_time is None:
        start_time = datetime.datetime.now()
        print("Timer started.")
    else:
        end_time = datetime.datetime.now()
        time_duration = (end_time - start_time).total_seconds() / 3600.0
        activity_dict[activity.lower()] += time_duration
        start_time = None
        print(f"{activity} time logged: {time_duration:.2f} hours")

The code now with an added print() function after line 33 which was missing to be able to output the time duration for the activity.
    
    if start_time is None:
      start_time = datetime.datetime.now()
      print("Timer started.")
    else:
      end_time = datetime.datetime.now()
      time_duration = (end_time - start_time).total_seconds() / 3600.0
      activity_dict[activity.lower()] += time_duration
      print(f"{activity} time logged: {time_duration:.2f} hours")
      start_time = None
       # If user inputs "done", show the time duration for the current activity
       if input("Type 'done' to stop tracking the current activity: ").lower() == 'done':
        print(f"{activity} time tracked: {activity_dict[activity.lower()]:.2f} hours")
        start_time = None

The code before:
# Loop to track activities
    while True:
    
    activity = input("What are you doing? (gaming/study/workout/commute/sleep) or type done to finish:  ")
    if activity.lower() not in activity_dict:
        print("Invalid activity. Please try again.")
        continue
     if start_time is None:
        start_time = datetime.datetime.now()
        print("Timer started.")
    else:
        end_time = datetime.datetime.now()
        time_duration = (end_time - start_time).total_seconds() / 3600.0
        activity_dict[activity.lower()] += time_duration
        start_time = None
        print(f"{activity} time logged: {time_duration:.2f} hours")
        
        # If user inputs "done", break out of loop
        if input("Are you done tracking activities for today? (y/n) ").lower() == 'y':
            Break

The code after
# Loop to track activities
    while True:

    activity = input("What are you doing? (gaming/study/workout/commute/sleep) or type done to finish:  ")
    if activity.lower() not in activity_dict:
        print("Invalid activity. Please try again.")
        continue
     if start_time is None:
        start_time = datetime.datetime.now()
        print("Timer started.")
        continue
    else:
        end_time = datetime.datetime.now()
        time_duration = (end_time - start_time).total_seconds() / 3600.0
        activity_dict[activity.lower()] += time_duration
        start_time = None
        print(f"{activity} time logged: {time_duration:.2f} hours")
        
        # If user inputs "done", break out of loop
        if input("Are you done tracking activities for today? (y/n) ").lower() == 'y':
            break


As you can see, the corrected code has a continue statement after printing "Timer started." in the if start_time is None: block. This continue statement skips the rest of the code in the else: block, which includes the input asking if the user is done tracking activities for today. This ensures that the correct input prompt is displayed at the appropriate time.

<h2>PART 5: Commenting Your Program</h2>
    import datetime
    from openpyxl import Workbook, load_workbook

    # Set up spreadsheet and sheet
    FILENAME = 'activity_log.xlsx'
    try:
      wb = load_workbook(FILENAME)
    except FileNotFoundError:
      wb = Workbook()
      wb.remove(wb.active)
    ws = wb.create_sheet('Activity Log')
    ws.append(['Date', 'Gaming', 'Workout', 'Study', 'Commute', 'Sleep', 'Idle'])

    # Initialize variables
    activity_dict = {'gaming': 0, 'workout': 0, 'study': 0, 'commute': 0, 'sleep': 0, 'gaming': 0}
    start_time = None
    end_tracking = False

    # Loop to track activities
    while not end_tracking:
    if start_time is None:
        activity = input("What are you doing? (gaming/workout/study/commute/sleep/work) (Type 'end' to finish tracking and get your output for the day): ")
        if activity.lower() not in activity_dict:
            print("Invalid activity. Please try again.")
            continue
        start_time = datetime.datetime.now()
        print("Timer started. Type 'done' if done tracking this activity or type 'end' to finish tracking for the day: ")
    else:
        done = input()
        while done.lower() not in ['done', 'end']:
            print("Invalid input. Please try again: ")
            done = input()
        if done.lower() == 'done':
            end_time = datetime.datetime.now()
            time_duration = (end_time - start_time).total_seconds() / 3600.0
            activity_dict[activity.lower()] += time_duration
            start_time = None
            print(f"{activity} time logged: {time_duration:.2f} hours")
        elif done.lower() == 'end':
            end_tracking = True

    # Calculate total time and percentage for each activity
    total_time = sum(activity_dict.values())
    activity_percentages = {activity: time / total_time for activity, time in activity_dict.items()}
    idle_time = 24 - total_time

    # Write data to spreadsheet
    date = datetime.date.today()
    ws.append([date, activity_dict['gaming'], activity_dict['workout'], activity_dict['study'], activity_dict['commute'], activity_dict['sleep'], idle_time])
    wb.save(FILENAME)

    # Print summary for user
    print(f"Activity log for {date}:")
    for activity, time in activity_dict.items():
      print(f"{activity.capitalize()}: {time:.2f} hours ({activity_percentages[activity] * 100:.2f}%)")
    print(f"Idle time: {idle_time:.2f} hours")

<h2>PART 6: Completed Program</h2>

https://replit.com/@v6tvm78p7w/Python-Time-Keeping-Project-AM#main.py


