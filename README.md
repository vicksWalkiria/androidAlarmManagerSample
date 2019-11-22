# androidAlarmManagerSample
A simple app to program and show notifications in all Android versions using AlarmManager. 
Just clone the project or copy and paste what you need.

Steps:

1. Create the alarm using the Alarm Manager

        AlarmManager alarmManager = (AlarmManager) ctx.getSystemService(ALARM_SERVICE);
        Intent alarmIntent = new Intent(ctx, AlarmReceiver.class);
        PendingIntent pendingIntent;
        pendingIntent = PendingIntent.getBroadcast(ctx, i, alarmIntent, PendingIntent.FLAG_ONE_SHOT);
        alarmIntent.setData((Uri.parse("custom://" + System.currentTimeMillis())));
        alarmManager.set(AlarmManager.RTC_WAKEUP, timestamp, pendingIntent);

Where i is the ID of the alarm and timestamp is the time you want it to get triggered.
Remember to add the permissions in you manifest:
        
        <uses-permission android:name="android.permission.WRITE_CALENDAR" />
        <uses-permission android:name="android.permission.READ_CALENDAR" />
        <uses-permission android:name="android.permission.FOREGROUND_SERVICE" />
        <uses-permission android:name="android.permission.WAKE_LOCK" />
        <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
        <uses-permission android:name="com.google.android.gms.permission.ACTIVITY_RECOGNITION" />
        <uses-permission android:name="android.permission.VIBRATE" />

2. Add these lines in your manifest inside the "application" tag

        <receiver
            android:name="com.walkiriaapps.alarmmanagersample.AlarmReceiver"
            android:enabled="true" />

        <service
            android:name="com.walkiriaapps.alarmmanagersample.NotificationService"
            android:enabled="true" />

Just change the package name for your own one.

3. Create the AlarmReceiver class. Remember to set it public.

4. Create the NotificationService class to display the notification when the alarm is triggered.

Happy coding ;).
