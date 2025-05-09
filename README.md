# Calorimeter
import customtkinter as ctk

import customtkinter as ctk


ctk.set_appearance_mode("light")


app = ctk.CTk()
app.title("Welcome to The Diet App")
app.geometry("600x400")


frame = ctk.CTkFrame(app, fg_color="#fff8e1")
frame.pack(fill="both", expand=True)

def show_main_menu():

    for widget in frame.winfo_children():
        widget.destroy()

    title_label = ctk.CTkLabel(frame, text="Welcome to The Diet App!", font=("Roboto", 20))
    title_label.pack(pady=20)


    diet_button = ctk.CTkButton(frame, text="Open Diet Tracker", command=open_diet_tracker)
    diet_button.pack(pady=10)

def open_diet_tracker():

    for widget in frame.winfo_children():
        widget.destroy()


    back_button = ctk.CTkButton(frame, text="← Back", command=show_main_menu, width=60)
    back_button.place(x=10, y=10)



    tracker_label = ctk.CTkLabel(frame, text="This is your Diet Tracker!", font=("Roboto", 18))
    tracker_label.pack(pady=60)


    track_calories_button = ctk.CTkButton(frame, text="Track Calories", command=open_track_calories)
    track_calories_button.pack(pady=10)



def open_track_calories():

    for widget in frame.winfo_children():
        widget.destroy()


    calories_label = ctk.CTkLabel(frame, text="Track Calories Screen", font=("Roboto", 35))
    calories_label.pack(pady=60)


    back_button = ctk.CTkButton(frame, text="← Back", command=open_diet_tracker, width=60)
    back_button.place(x=10, y=10)
if():
    ctk.set_appearance_mode("light")


DAILY_GOAL = 2200
current_calories = 0



app = ctk.CTk()
app.title("Calorie Tracker")
app.geometry("600x400")


progress_bar = ctk.CTkProgressBar(app, width=300)
progress_bar.set(0)
progress_bar.pack(pady=20)


label = ctk.CTkLabel(app, text=f"Calories: 0 / {DAILY_GOAL}", font=ctk.CTkFont(size=16))
label.pack(pady=10)


calorie_entry = ctk.CTkEntry(app, placeholder_text="Enter calories eaten")
calorie_entry.pack(pady=10)


def update_calories():
    global current_calories
    try:
        calories = int(calorie_entry.get())
        current_calories += calories
        if current_calories > DAILY_GOAL:
            current_calories = DAILY_GOAL


        progress = current_calories / DAILY_GOAL
        progress_bar.set(progress)
        label.configure(text=f"Calories: {current_calories} / {DAILY_GOAL}")

        if current_calories == DAILY_GOAL:
            done_label = ctk.CTkLabel(app, text="🎉 Goal Reached!", font=ctk.CTkFont(size=18, weight="bold"))
            done_label.pack(pady=10)

    except ValueError:
        label.configure(text="Please enter a valid number.")


button = ctk.CTkButton(app, text="Add Calories", command=update_calories)
button.pack(pady=10)


app.mainloop()
