---
dg-publish: true
dg-created: Jun 13, 2024, 10:36 AM
---

# Add "Media created" Tag

1. **Open PowerShell**: Open PowerShell by pressing `Win + X`, then selecting `Windows PowerShell` or `Windows PowerShell (Admin)`.

2. **Check if `$PROFILE` exists**: Check if the profile file exists by typing:

```powershell
Test-Path $PROFILE
```

If it returns `False`, the profile file does not exist and you need to create it.

3. **Create the `$PROFILE` file**: Create the profile file by typing:
```powershell
New-Item -Path $PROFILE -Type File -Force
```

This command creates the profile file at the path specified by `$PROFILE`.

4. **Open the `$PROFILE` file in Notepad**: Open the newly created profile file in Notepad:
```powershell
notepad $PROFILE
```

5. **Add the Function to Your Profile**:

Paste the following code into the Notepad window that opens:

```powershell
function Update-MP4Dates {
    # Regular expression pattern to match the date and AM/PM in the filename
    $datePattern = "^\d{3} - (\d{2}-\d{2}-\d{4}) (AM|PM) - .*"

    # Iterate over each MP4 file in the current directory
    Get-ChildItem -File -Filter *.mp4 | ForEach-Object {
        $filename = $_.Name
        if ($filename -match $datePattern) {
            $dateString = $matches[1]
            $timeOfDay = $matches[2]

            # Parse the date string
            $date = [datetime]::ParseExact($dateString, "MM-dd-yyyy", $null)

            # Set the time based on AM/PM
            if ($timeOfDay -eq "AM") {
                $date = $date.AddHours(16).AddMinutes(30)  # Set time to 10:30 AM
            } elseif ($timeOfDay -eq "PM") {
                $date = $date.AddHours(24)  # Set time to 6:00 PM
            }

            # Format the date as required by exiftool
            $newDate = $date.ToString("yyyy:MM:dd HH:mm:ss")

            # Update the media created date using exiftool
            exiftool -AllDates="$newDate" -overwrite_original $_.FullName
            Write-Output "Updated $filename to $newDate"
        } else {
            Write-Output "Skipped $filename - No matching date found"
        }
    }
}

# Create an alias for the function
Set-Alias UpdateDates Update-MP4Dates
```

6. **Save and Close Notepad**: Save the changes and close Notepad.

7. **Reload Your Profile**:

After saving the file, reload your PowerShell profile to apply the changes:
```powershell
. $PROFILE
```

### Using the Alias

Now, you can navigate to any directory containing your MP4 files and run the function by simply typing the alias `UpdateDates`:

```powershell
cd C:\path\to\your\directory
UpdateDates
```

This setup allows you to update the "Media created" dates of MP4 files in the current directory by extracting the date from the filename, making it convenient to use from any location within PowerShell.

![](https://i.imgur.com/ghe9L4c.png)

# Add Metadata

```powershell
function AddMetadata {
    # Set the regex pattern to match the filename format
    $filenamePattern = '(\d{3}) - (\d{2})-(\d{2})-(\d{4}) (AM|PM) - (.*)'

    # Get all MP4 files matching the pattern in the current directory
    $files = Get-ChildItem -File -Filter *.mp4 | Where-Object { $_.Name -match $filenamePattern }
    foreach ($file in $files) {
        $filename = $file.Name

        # Extract information from the filename using regex groups
        if ($filename -match $filenamePattern) {
            $track = $matches[1]
            $month = $matches[2]
            $day = $matches[3]
            $year = $matches[4]
            $timeOfDay = $matches[5]
            $title = $matches[6]

            # Determine service time based on AM/PM
            if ($timeOfDay -eq "AM") {
                $serviceTime = "10:30 AM"
            } elseif ($timeOfDay -eq "PM") {
                $serviceTime = "6:00 PM"
            } else {
                $serviceTime = "Unknown"
            }

            # Parse the date string
            $dateString = "$month-$day-$year"
            $date = [datetime]::ParseExact($dateString, "MM-dd-yyyy", $null)

            # Adjust the time based on AM/PM
            if ($timeOfDay -eq "AM") {
                $date = $date.AddHours(16).AddMinutes(30)  # Set time to 10:30 AM
            } elseif ($timeOfDay -eq "PM") {
                $date = $date.AddHours(24)  # Set time to 6:00 PM
            }

            # Format the date as required by exiftool
            $newDate = $date.ToString("yyyy:MM:dd HH:mm:ss")

            # Construct the comment string
            $comment = "Preached by Pastor Steven Anderson at Faithful Word Baptist Church on $month/$day/$year for the $serviceTime service."

            # Set metadata using exiftool
            exiftool `
                -Title="$title" `
                -Comment="$comment" `
                -TrackNumber="$track" `
                -AllDates="$newDate" `
                -Year="$year" `
                -overwrite_original `
                $file.FullName

            Write-Output "Updated metadata for $($file.Name)"
        } else {
            Write-Output "Skipped $($file.Name) - Filename does not match expected pattern"
        }
    }
}

# Create an alias for the function
Set-Alias AddMetadataFunction AddMetadata
```