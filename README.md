📌 Features of Multi-Process Task Scheduler (Like cron)

- Job Scheduling – Run tasks at specific time intervals (e.g., every minute, hourly, daily).
- Multi-Processing – Each scheduled task runs as a separate process.
- Configuration File Support – Read task schedules from a config file (like crontab).
- Logging System – Maintain logs of executed tasks with timestamps.
- Signal Handling – Gracefully handle task termination (SIGCHLD, SIGTERM).
- Inter-Process Communication (IPC) – Use pipes or shared memory for reporting task status.
- Task Prioritization (Optional) – Support priority-based scheduling (higher priority tasks run first).

----

🛠️ Approach to Building the Project

1. Understanding Process Scheduling:

    Research how cron works and how processes are scheduled in Linux.
    Decide if tasks should run at fixed intervals or support flexible scheduling.

2. Designing the Task Scheduler:

    Maintain a task queue (array, linked list, or priority queue).
    Read scheduled tasks from a configuration file (custom format or crontab-like syntax).

3. Implementing Multi-Processing:

    Use fork() to create a separate process for each scheduled task.
    Handle zombie processes using waitpid().

4. Inter-Process Communication (IPC):

    Use pipes, shared memory, or message queues for task reporting.
    Example: A child process reports task execution status to the parent.

5. Handling Signals:

    Use SIGCHLD to handle child process termination.
    Implement SIGTERM to allow graceful shutdown of the scheduler.

6. Logging System:

    Maintain execution logs for debugging and monitoring.
    Store logs in a file or use syslog().

7. Testing & Optimization:

    Test with different types of tasks (CPU-bound, I/O-bound).
    Optimize process management to reduce overhead.
