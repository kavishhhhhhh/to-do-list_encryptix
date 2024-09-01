# to-do-list_encryptix
def display_menu():
    print("\nTo-Do List Menu:")
    print("1. View To-Do List")
    print("2. Add a Task")
    print("3. Remove a Task")
    print("4. Mark a Task as Completed")
    print("5. Exit")

def view_todo_list(todo_list):
    if not todo_list:
        print("\nYour To-Do list is empty.")
    else:
        print("\nYour To-Do List:")
        for index, task in enumerate(todo_list, start=1):
            status = "Done" if task['completed'] else "Not Done"
            print(f"{index}. {task['task']} - [{status}]")

def add_task(todo_list):
    task = input("\nEnter the task you want to add: ")
    todo_list.append({"task": task, "completed": False})
    print(f"Task '{task}' has been added to your To-Do list.")

def remove_task(todo_list):
    try:
        task_number = int(input("\nEnter the task number you want to remove: "))
        if 0 < task_number <= len(todo_list):
            removed_task = todo_list.pop(task_number - 1)
            print(f"Task '{removed_task['task']}' has been removed.")
        else:
            print("Invalid task number. Please try again.")
    except ValueError:
        print("Please enter a valid number.")

def mark_task_completed(todo_list):
    try:
        task_number = int(input("\nEnter the task number you want to mark as completed: "))
        if 0 < task_number <= len(todo_list):
            todo_list[task_number - 1]['completed'] = True
            print(f"Task '{todo_list[task_number - 1]['task']}' has been marked as completed.")
        else:
            print("Invalid task number. Please try again.")
    except ValueError:
        print("Please enter a valid number.")

def todo_list_app():
    todo_list = []

    while True:
        display_menu()
        choice = input("\nEnter your choice (1-5): ")

        if choice == '1':
            view_todo_list(todo_list)
        elif choice == '2':
            add_task(todo_list)
        elif choice == '3':
            remove_task(todo_list)
        elif choice == '4':
            mark_task_completed(todo_list)
        elif choice == '5':
            print("Exiting the To-Do List application. Goodbye!")
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 5.")
todo_list_app()
