class ToDoList:
    def _init_(self):
        self.tasks = []

    def add_task(self, task):
        self.tasks.append({"task": task, "completed": False})

    def view_tasks(self):
        if not self.tasks:
            print("No tasks in the list.")
        else:
            print("Tasks:")
            for idx, task in enumerate(self.tasks, start=1):
                status = "X" if task["completed"] else " "
                print(f"{idx}. [{status}] {task['task']}")

    def complete_task(self, task_index):
        if 1 <= task_index <= len(self.tasks):
            self.tasks[task_index - 1]["completed"] = True
            print(f"Task {task_index} marked as completed.")
        else:
            print("Invalid task number.")

    def remove_task(self, task_index):
        if 1 <= task_index <= len(self.tasks):
            del self.tasks[task_index - 1]
            print(f"Task {task_index} removed.")
        else:
            print("Invalid task number.")

def main():
    todo_list = ToDoList()

    while True:
        print("\nOptions:")
        print("1. Add Task")
        print("2. View Tasks")
        print("3. Complete Task")
        print("4. Remove Task")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            task = input("Enter task: ")
            todo_list.add_task(task)
        elif choice == '2':
            todo_list.view_tasks()
        elif choice == '3':
            task_index = int(input("Enter task number to mark as completed: "))
            todo_list.complete_task(task_index)
        elif choice == '4':
            task_index = int(input("Enter task number to remove: "))
            todo_list.remove_task(task_index)
        elif choice == '5':
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please enter a number from 1 to 5.")

if _name_ == "_main_":
    main()
