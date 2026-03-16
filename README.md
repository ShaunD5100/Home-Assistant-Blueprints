## Washing Machine Finished Blueprint

### Blueprint Name: Washing Machine Finished (Power Monitor + Repeat Reminder + Door/Vibration Stop + Cooldown)

This blueprint monitors power usage to ensure efficient laundry cycles. It provides notifications when the washing machine has finished its cycle and includes various features to enhance the monitoring process.

### Key Features:
- **Power Monitoring**: Keeps track of the machine's power usage during the cycle.
- **Repeat Reminders**: Sends notifications at regular intervals if laundry isn't removed.
- **Door/Vibration Sensors**: Detects if the laundry door is open or if vibration is detected, alerting the user accordingly.
- **Cooldown Functionality**: Prevents operation during cooldown periods to save energy and extend the machine's life.

### Use Cases:
- Monitoring laundry cycles effectively.
- Ensuring that laundry is promptly removed to prevent mildew or other issues.

### Configuration Parameters:
- `power_sensor`: Sensor to monitor the power usage.
- `running_threshold`: The threshold for determining if the machine is running.
- `finished_threshold`: The threshold for determining if the cycle has finished.
- `finished_duration`: Duration to confirm that the cycle has finished.
- `notify_service`: Service to send notifications.
- `message`: Message to be sent upon cycle completion.
- `enable_repeat`: Option to enable repeat reminders.
- `repeat_interval`: Interval for repeat reminders.
- `door_sensor`: Sensor to check if the door is open.
- `vibration_sensor`: Sensor to detect vibrations indicating the machine is still running.
- `enable_cooldown`: Option to enable or disable cooldown periods.
- `cooldown_duration`: Duration of the cooldown period before the machine can be restarted.

