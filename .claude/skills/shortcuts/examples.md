# macOS Shortcuts Skill - Examples

This document provides detailed examples of using the macOS Shortcuts skill in various scenarios.

## Scenario 1: Discovering Available Shortcuts

**User Request:**
"What shortcuts do I have available?"

**Claude's Response:**
```bash
shortcuts list
```

**Expected Output:**
```
My Morning Routine
Weekly Report Generator
Resize Images
Convert to PDF
Send Email Summary
Process Screenshots
Text to Speech
Translate Text
Create Meeting Notes
Backup Project Files
```

## Scenario 2: Running a Simple Shortcut

**User Request:**
"Run my Morning Routine shortcut"

**Claude's Response:**
```bash
shortcuts run "My Morning Routine"
```

**Expected Output:**
```
[Output depends on what the shortcut does]
Morning routine completed!
```

## Scenario 3: Viewing a Shortcut's Configuration

**User Request:**
"Show me how the Weekly Report Generator shortcut works"

**Claude's Response:**
```bash
shortcuts view "Weekly Report Generator"
```

**Expected Output:**
The Shortcuts app will open with the "Weekly Report Generator" shortcut displayed for editing/viewing.

## Scenario 4: Running a Shortcut with File Input

**User Request:**
"Use the Resize Images shortcut to process photo.jpg"

**Claude's Response:**
```bash
shortcuts run "Resize Images" --input-path /Users/username/Documents/photo.jpg
```

**Expected Output:**
```
Image resized successfully!
Output saved to: /Users/username/Documents/photo_resized.jpg
```

## Scenario 5: Running a Shortcut with Text Input

**User Request:**
"Translate 'Hello, how are you?' using my Translate Text shortcut"

**Claude's Response:**
```bash
echo "Hello, how are you?" | shortcuts run "Translate Text"
```

**Expected Output:**
```
Hola, ¿cómo estás?
```

## Scenario 6: Handling Non-Existent Shortcuts

**User Request:**
"Run the Backup Database shortcut"

**Claude's First Response:**
```bash
shortcuts run "Backup Database"
```

**Error Output:**
```
The shortcut "Backup Database" could not be found.
```

**Claude's Recovery:**
"Let me check what shortcuts are available:"
```bash
shortcuts list
```

**Claude's Follow-up:**
"I don't see a shortcut named 'Backup Database'. You have these shortcuts available: [list]. Did you mean one of these?"

## Scenario 7: Processing Multiple Files

**User Request:**
"Convert all PDFs in the current directory using my Convert to PDF shortcut"

**Claude's Response:**
```bash
for file in *.pdf; do
  echo "Processing $file..."
  shortcuts run "Convert to PDF" --input-path "$file"
done
```

## Scenario 8: Shortcut with Complex Output

**User Request:**
"Run my Process Screenshots shortcut"

**Claude's Response:**
```bash
shortcuts run "Process Screenshots"
```

**Expected Output:**
```
Processing screenshot_1.png...
Processing screenshot_2.png...
Processing screenshot_3.png...

Processed 3 screenshots
Saved to: ~/Pictures/Processed/
Created collage: ~/Pictures/Processed/collage.png
```

## Scenario 9: Interactive Workflow

**User Request:**
"I need to prepare my weekly report"

**Claude's Response:**
"I can help with that. Let me check if you have a shortcut for weekly reports:"

```bash
shortcuts list
```

**After seeing the output:**
"I found 'Weekly Report Generator'. Would you like me to run it?"

**User:** "Yes"

**Claude's Response:**
```bash
shortcuts run "Weekly Report Generator"
```

## Scenario 10: Combining Shortcuts with Other Commands

**User Request:**
"Create a backup of my project and then run my Backup Project Files shortcut"

**Claude's Response:**
```bash
# First create a local backup
tar -czf project_backup.tar.gz ./src

# Now run the shortcut to upload it
shortcuts run "Backup Project Files" --input-path ./project_backup.tar.gz
```

**Expected Output:**
```
Backup uploaded successfully!
Stored at: iCloud Drive/Backups/project_backup.tar.gz
```

## Tips for Using Examples

1. **Always list first when unsure:** If you're not certain of the exact shortcut name, list all shortcuts first
2. **Verify file paths:** When using --input-path, make sure the file exists and use absolute or correct relative paths
3. **Check permissions:** Some shortcuts may require permissions that need to be granted in System Preferences
4. **Handle spaces:** Always use quotes around shortcut names that contain spaces
5. **Error handling:** If a shortcut fails, check the Shortcuts app to see if it has any configuration issues

## Common Patterns

### Pattern 1: List → View → Run
```bash
# 1. List all shortcuts
shortcuts list

# 2. View a specific one to understand it
shortcuts view "Shortcut Name"

# 3. Run it
shortcuts run "Shortcut Name"
```

### Pattern 2: Batch Processing
```bash
# Process multiple files
for file in *.jpg; do
  shortcuts run "Process Image" --input-path "$file"
done
```

### Pattern 3: Pipeline Integration
```bash
# Use shortcuts in a pipeline
cat data.txt | shortcuts run "Format Data" > formatted.txt
```

### Pattern 4: Conditional Execution
```bash
# Run shortcut only if file exists
if [ -f "report.pdf" ]; then
  shortcuts run "Send Report" --input-path "report.pdf"
fi
```
