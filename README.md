# astronut
for program
using System;
using System.Collections.Generic;

namespace AstronautSchedule
{
    class Task
    {
        public string Description { get; set; }
        public DateTime StartTime { get; set; }
        public DateTime EndTime { get; set; }
        public int Priority { get; set; }

        public Task(string description, DateTime startTime, DateTime endTime, int priority)
        {
            Description = description;
            StartTime = startTime;
            EndTime = endTime;
            Priority = priority;
        }
    }

    class Program
    {
        static List<Task> tasks = new List<Task>();

        static void Main(string[] args)
        {
            bool running = true;

            while (running)
            {
                Console.WriteLine("\nAstronaut Schedule Organizer");
                Console.WriteLine("1. Add Task");
                Console.WriteLine("2. Remove Task");
                Console.WriteLine("3. View Tasks");
                Console.WriteLine("4. Exit");

                Console.Write("Enter your choice: ");
                int choice = int.Parse(Console.ReadLine());

                switch (choice)
                {
                    case 1:
                        AddTask();
                        break;
                    case 2:
                        RemoveTask();
                        break;
                    case 3:
                        ViewTasks();
                        break;
                    case 4:
                        running = false;
                        break;
                    default:
                        Console.WriteLine("Invalid choice.");
                        break;
                }
            }
        }

        static void AddTask()
        {
            Console.Write("Enter task description: ");
            string description = Console.ReadLine();
            Console.Write("Enter start time (YYYY-MM-DD HH:MM): ");
            DateTime startTime = DateTime.Parse(Console.ReadLine());
            Console.Write("Enter end time (YYYY-MM-DD HH:MM): ");
            DateTime endTime = DateTime.Parse(Console.ReadLine());
            Console.Write("Enter priority (1-5): ");
            int priority = int.Parse(Console.ReadLine());

            tasks.Add(new Task(description, startTime, endTime, priority));
            Console.WriteLine("Task added successfully.");
        }

        static void RemoveTask()
        {
            Console.Write("Enter task index to remove: ");
            int index = int.Parse(Console.ReadLine());

            if (index >= 0 && index < tasks.Count)
            {
                tasks.RemoveAt(index);
                Console.WriteLine("Task removed successfully.");
            }
            else
            {
                Console.WriteLine("Invalid task index.");
            }
        }

        static void ViewTasks()
        {
            if (tasks.Count == 0)
            {
                Console.WriteLine("No tasks found.");
            }
            else
            {
                Console.WriteLine("Tasks:");
                for (int i = 0; i < tasks.Count; i++)
                {
                    Console.WriteLine($"{i + 1}. {tasks[i].Description} - {tasks[i].StartTime} - {tasks[i].EndTime} - Priority: {tasks[i].Priority}");
                }
            }
        }
    }
}
