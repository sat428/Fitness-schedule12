<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>18-Minute Fitness Schedule</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f9;
            color: #333;
        }
        header {
            background-color: #007BFF;
            color: white;
            padding: 20px 0;
            text-align: center;
        }
        main {
            padding: 20px;
            max-width: 800px;
            margin: auto;
        }
        section {
            margin-bottom: 20px;
        }
        h2 {
            color: #007BFF;
        }
        .checkbox-group {
            margin-top: 10px;
        }
        .checkbox-group label {
            margin-right: 15px;
        }
        footer {
            text-align: center;
            padding: 10px 0;
            background-color: #333;
            color: white;
        }
        .reminder {
            margin-top: 20px;
            padding: 10px;
            background-color: #e9ecef;
            border-left: 5px solid #007BFF;
        }
    </style>
</head>
<body>
    <header>
        <h1>18-Minute Fitness Schedule</h1>
        <p>Plank & Push-ups Routine</p>
    </header>
    <main>
        <section>
            <h2>Morning Session (6 Minutes)</h2>
            <ul>
                <li>Plank: 2 minutes</li>
                <li>Push-ups: 2 minutes (3 sets of 10-15 reps)</li>
                <li>Rest: 2 minutes</li>
            </ul>
            <div class="checkbox-group">
                <label for="morning">Morning Completed</label>
                <input type="checkbox" id="morning" onclick="trackProgress()">
            </div>
        </section>
        <section>
            <h2>Afternoon Session (6 Minutes)</h2>
            <ul>
                <li>Plank: 3 minutes</li>
                <li>Push-ups: 3 minutes (4 sets of 10-15 reps)</li>
            </ul>
            <div class="checkbox-group">
                <label for="afternoon">Afternoon Completed</label>
                <input type="checkbox" id="afternoon" onclick="trackProgress()">
            </div>
        </section>
        <section>
            <h2>Evening Session (6 Minutes)</h2>
            <ul>
                <li>Plank: 2 minutes</li>
                <li>Push-ups: 2 minutes (3 sets of 10-15 reps)</li>
                <li>Rest: 2 minutes</li>
            </ul>
            <div class="checkbox-group">
                <label for="evening">Evening Completed</label>
                <input type="checkbox" id="evening" onclick="trackProgress()">
            </div>
        </section>
        <div class="reminder">
            <p>Stay consistent and hydrate!</p>
        </div>
    </main>
    <footer>
        <p>Fitness Routine | Get Strong!</p>
    </footer>

    <script>
        // Reminder for the user at specific times of day
        function sendReminder() {
            if (Notification.permission === "granted") {
                new Notification("Time for your fitness routine!");
            }
        }

        // Request Notification permission
        if (Notification.permission !== "granted") {
            Notification.requestPermission();
        }

        // Set reminders at certain times (example: 9 AM, 1 PM, 6 PM)
        setInterval(() => {
            const now = new Date();
            if (now.getHours() === 9 && now.getMinutes() === 0) {
                sendReminder();
            }
            if (now.getHours() === 13 && now.getMinutes() === 0) {
                sendReminder();
            }
            if (now.getHours() === 18 && now.getMinutes() === 0) {
                sendReminder();
            }
        }, 60000); // Check every minute

        // Track completed sessions
        function trackProgress() {
            const morningChecked = document.getElementById('morning').checked;
            const afternoonChecked = document.getElementById('afternoon').checked;
            const eveningChecked = document.getElementById('evening').checked;

            if (morningChecked && afternoonChecked && eveningChecked) {
                alert("Awesome! You've completed your fitness routine for today!");
            }
        }
    </script>
</body>
</html>
