# Home Assistant Blueprints

Welcome to the Home Assistant Blueprints repository! This collection contains reusable automation blueprints designed to extend and enhance your Home Assistant smart home setup.

## 📋 Available Blueprints

### Entity State Duration Notification
**File:** `entity_state_duration_notification.yaml`

A powerful automation blueprint that sends notifications when a selected entity remains in a specific state (ON or OFF) for longer than a configured duration.

#### Features
- 🔔 **State Monitoring**: Monitor any Home Assistant entity for prolonged state changes
- ⏱️ **Customizable Duration**: Set how long an entity must stay in a state before triggering
- 📬 **Flexible Notifications**: Send notifications to any notification service
- ⏰ **Time-Based Restrictions**: Optionally restrict alerts to specific hours
- 🎨 **Custom Messages**: Personalize notification messages with template support
- 🔄 **Reliable Execution**: Uses `mode: single` to prevent duplicate triggers

#### Use Cases
- Alert when a door or window has been open for too long
- Notify when a light has been on longer than expected
- Monitor if a device remains offline or connected for extended periods
- Track when water or appliances are running longer than normal

#### Configuration

1. **Copy the blueprint file** to your Home Assistant blueprints directory:
   ```
   config/blueprints/automation/
   ```

2. **Reload blueprints** in Home Assistant or restart the service

3. **Create a new automation** from the Home Assistant UI:
   - Go to Settings → Automations & Scenes
   - Click "Create Automation"
   - Select "Create from Blueprint"
   - Choose "Notify if entity stays in a chosen state for too long"

#### Parameters

| Parameter | Description | Default | Required |
|-----------|-------------|---------|----------|
| **Entity to monitor** | The entity whose state you want to track | - | Yes |
| **State to monitor** | Trigger when entity is in "on" or "off" state | `off` | Yes |
| **Duration** | How long the entity must stay in the chosen state | `01:00:00` | Yes |
| **Notification service** | The notify service to call (e.g., `notify.mobile_app_phone`) | - | Yes |
| **Notification message** | Custom message text with template support | Auto-generated | No |
| **Restrict to certain hours?** | Enable time-based alert restrictions | `false` | No |
| **Start time** | Earliest time to send alerts (24-hour format) | `00:00:00` | No |
| **End time** | Latest time to send alerts (24-hour format) | `23:59:59` | No |

#### Example Usage

**Scenario 1: Alert if Front Door Open Too Long**
- Entity: `binary_sensor.front_door`
- State: `on`
- Duration: `00:10:00` (10 minutes)
- Service: `notify.mobile_app_phone`
- Message: `Front door has been open for over 10 minutes!`

**Scenario 2: Alert if Office Light Left On**
- Entity: `light.office`
- State: `on`
- Duration: `02:00:00` (2 hours)
- Service: `notify.mobile_app_phone`
- Restrict time: `true`
- Start: `22:00:00` (10 PM)
- End: `08:00:00` (8 AM)
- Message: `Office light has been on all night!`

#### Message Templating

You can use Jinja2 templates in the notification message. Available variables:
- `{{ trigger.entity_id }}` - The entity ID that triggered the notification
- `{{ target_state }}` - The state being monitored
- `{{ duration }}` - The duration configured

Example: "{{ trigger.entity_id }} has been {{ target_state }} for over {{ duration }}."

## 🚀 Getting Started

1. **Prerequisites**
   - Home Assistant 2021.12 or later
   - At least one automation-capable entity

2. **Installation**
   - Clone or download this repository
   - Copy blueprint files to `config/blueprints/automation/`
   - Reload automations in Home Assistant

3. **Create Your First Automation**
   - Use the Home Assistant UI to create automations from these blueprints
   - Customize parameters to fit your needs

## 📝 Template Variables

These blueprints support Jinja2 templating for advanced customization. Common variables:
- `{{ trigger }}` - Trigger details
- `{{ now() }}` - Current time
- `{{ states('entity_id') }}` - Current state of any entity

## 🛠️ Troubleshooting

**Blueprint not showing up?**
- Ensure the file is in the correct directory: `config/blueprints/automation/`
- Reload automations: Developer Tools → YAML → Automations
- Check YAML syntax using the YAML checker in Home Assistant

**Automation not triggering?**
- Verify the entity ID is correct
- Check that the state matches exactly (case-sensitive)
- Review automation history in Home Assistant

**Notifications not sending?**
- Confirm the notification service is correct (e.g., `notify.mobile_app_phone`)
- Test the service manually in Developer Tools → Services
- Check Home Assistant logs for errors

## 📚 Resources

- [Home Assistant Blueprints Documentation](https://www.home-assistant.io/docs/automation/using_blueprints/)
- [Home Assistant Automation Documentation](https://www.home-assistant.io/docs/automation/)
- [Jinja2 Templating Guide](https://www.home-assistant.io/docs/configuration/templating/)

## 🤝 Contributing

Found a bug or have an improvement? Feel free to:
- Open an issue to report problems
- Submit pull requests with enhancements
- Share your usage examples

## 📄 License

These blueprints are provided as-is for use with Home Assistant.

## 💡 Tips & Best Practices

1. **Start Simple**: Begin with default parameters and customize as needed
2. **Test First**: Create a test automation before deploying to production
3. **Use Descriptions**: Add descriptive names and notes to your automations for future reference
4. **Monitor Logs**: Check Home Assistant logs for debugging
5. **Time Restrictions**: Use time restrictions to reduce notification fatigue

---

Happy automating! 🏠✨