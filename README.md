# 🕐 Cronjobber an Advanced Cron Job Code Generator

A powerful, interactive web-based tool for creating, testing, and visualizing cron job schedules. Generate production-ready code in multiple languages with a beautiful, user-friendly interface. See it in action at **[jordibrw.nl](https://www.jordibrw.nl/projects/cron-generator.html)**.

## Features

✨ **Interactive Cron Builder**
- Simple input fields for all 5 cron fields (minute, hour, day of month, month, day of week)
- Preset selectors for common schedules
- Real-time validation with visual feedback

🌍 **Natural Language Support**
- Parse Dutch and English descriptions into cron expressions
- Examples: "elke werkdag om 9:00" or "every weekday at 9 AM"

💻 **Multi-Language Code Generation**
- **Bash**: Direct crontab commands and installation scripts
- **Node.js**: node-cron implementation with examples
- **Python**: APScheduler integration code
- **Java**: Quartz scheduler configuration
- **Docker/Kubernetes**: Docker Compose and Kubernetes CronJob definitions

📊 **Advanced Visualization**
- Next 50 scheduled run times with timezone support
- 365-day heat map showing execution frequency distribution
- Real-time human-readable description of schedules

🎯 **50+ Quick Presets**
Including:
- Hourly, daily, weekly, monthly, quarterly, and yearly patterns
- Business hours, weekend, and off-hours schedules
- Backup windows and maintenance schedules
- Common polling intervals

🔧 **Developer Tools**
- Copy code to clipboard with one click
- Download generated code files
- Test run console to preview next scheduled executions
- Save favorite schedules to browser storage

🌐 **Timezone Support**
- Select from major timezones (UTC, Europe/Amsterdam, America/New_York, etc.)
- View next runs in your preferred timezone

## Quick Start

### Option 1: Online Version
Simply open `cron-generator.html` in any modern web browser.

### Option 2: GitHub Pages
Host the file on GitHub Pages for easy sharing and access.

## Usage

1. **Build Your Schedule**
   - Adjust the Cron Fields on the left (minute, hour, day, month, day of week)
   - Use preset dropdowns for quick selections
   - Or enter a natural language description and click "Parse"

2. **Review & Validate**
   - Check the green validation badge (✅ = valid, ❌ = invalid)
   - Read the human-readable description
   - View the next 50 scheduled execution times
   - Check the 365-day frequency heat map

3. **Generate Code**
   - Select your preferred language from the tabs
   - Review the generated code template
   - Copy to clipboard or download the file
   - Customize as needed for your environment

4. **Test & Save**
   - Click "Test Run" to see next executions in the browser console
   - Save your favorite schedules for quick access later

## Cron Expression Format

The standard cron format with 5 fields:

```
┌───────────── minute (0 - 59)
│ ┌───────────── hour (0 - 23)
│ │ ┌───────────── day of month (1 - 31)
│ │ │ ┌───────────── month (1 - 12)
│ │ │ │ ┌───────────── day of week (0 - 6) (0 = Sunday)
│ │ │ │ │
│ │ │ │ │
* * * * * command
```

### Special Characters

- `*` - any value
- `,` - value list separator (e.g., `1,3,5`)
- `-` - range (e.g., `1-5`)
- `/` - step values (e.g., `*/5`)

### Examples

| Schedule | Cron Expression | Description |
|----------|-----------------|-------------|
| Every minute | `* * * * *` | Runs every minute |
| Every 5 minutes | `*/5 * * * *` | Runs every 5 minutes |
| Daily at 9 AM | `0 9 * * *` | Every day at 9:00 AM |
| Weekdays at 9 AM | `0 9 * * 1-5` | Monday-Friday at 9:00 AM |
| First of month | `0 0 1 * *` | 1st day of each month at midnight |
| Every Monday | `0 9 * * 1` | Mondays at 9:00 AM |

## Technologies Used

- **Frontend**: HTML5, CSS3, JavaScript (Vanilla)
- **Styling**: Tailwind CSS
- **Canvas**: Custom heat map visualization

## Browser Support

Works in all modern browsers:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## Code Examples

### Bash / Crontab
```bash
# Add to crontab
crontab -e
# Then add your cron expression:
0 9 * * * /path/to/script.sh
```

### Node.js
```javascript
const cron = require('node-cron');

cron.schedule('0 9 * * *', () => {
    console.log('Running scheduled task');
    // Your code here
});
```

### Python
```python
from apscheduler.schedulers.blocking import BlockingScheduler

scheduler = BlockingScheduler()

@scheduler.scheduled_job('cron', hour=9)
def scheduled_job():
    print('Running task')
    # Your code here

scheduler.start()
```

### Docker/Kubernetes
```yaml
apiVersion: batch/v1
kind: CronJob
metadata:
  name: my-scheduled-job
spec:
  schedule: "0 9 * * *"
  jobTemplate:
    spec:
      template:
        spec:
          containers:
          - name: job
            image: my-image:latest
          restartPolicy: OnFailure
```

## Local Development

To enhance or modify the tool:

1. Clone the repository
2. Open `cron-generator.html` in your browser
3. Edit the HTML/CSS/JavaScript as needed
4. Test in real-time in the browser

### File Structure
```
.
├── cron-generator.html    # Main application file
├── README.md              # This file
└── Cronjob.code-workspace # VS Code workspace configuration
```

## Features Explained

### Cron Validation
The tool validates cron expressions in real-time:
- Checks for empty fields
- Validates numerical ranges
- Parses complex expressions (ranges, steps, lists)

### Heat Map Visualization
The 365-day heat map shows:
- Green cells = frequent execution periods
- Red cells = infrequent execution periods
- Helps identify execution patterns at a glance

### Natural Language Parser
Supports multiple languages:
- Dutch: "elke werkdag", "eerste van de maand", "om 9:00"
- English: "every weekday", "first of month", "at 9 AM"

## Troubleshooting

**Issue: Cron expression shows as invalid**
- Check that all 5 fields have values (use `*` for wildcards)
- Ensure numbers are within valid ranges
- Verify special characters are used correctly

**Issue: Generated code doesn't work**
- Ensure the target language dependencies are installed
- Check timezone settings if times seem off
- Review the code template for placeholders that need customization

**Issue: Next runs look incorrect**
- Verify your timezone is set correctly
- Check the cron expression is what you intended
- Consider daylight saving time changes

## Contributing

Contributions are welcome! Feel free to:
- Report bugs and issues
- Suggest new features
- Improve documentation
- Add more language code templates

## License

MIT License - Feel free to use this tool commercially and personally.

## Author

Created with ❤️ for developers managing scheduled tasks.

---

**Pro Tips:**
- Use the 50+ presets as starting points for your custom schedules
- Always test your cron expressions with the Test Run feature before deployment
- Save frequently-used schedules as favorites
- Use timezone selector to ensure times are correct in your deployment region
