# Overview
Notifications Scripting is a GUI-less application that can be only used with AppleScript. This application allows AppleScript scripts to display user notifications since OS X Mountain Lion and handle the user interactions with these notifications.

# Screenshot
<img width="378" height="118" alt="Capture d’écran 2026-03-19 à 19 03 13" src="https://github.com/user-attachments/assets/594907ba-5e7e-4160-ba5d-435681db116d" />

# AppleScript Dictionary
<img width="1121" height="1067" alt="Capture d’écran 2026-03-19 à 19 09 42" src="https://github.com/user-attachments/assets/e96430ec-591c-4306-bb9c-10be314a7ff5" />

# Usage
```applescript
tell application "Notifications Scripting"

	-- Display a window with event handler results (for debugging purposes).
	set show event handler results to true

	--  This is required for calling the user notification event handlers. The handlers can be in a different script file. If not defined, the event handlers will not be called.
	set event handlers script path to (path to me)

	-- Create a notification. Only the title is required at minimum.
	-- Use "Default" for the default sound played by the user notification center.
	-- See the Notifications Scripting dictionary for more informations.
	display notification "My message" with title "My title" subtitle "My subtitle"

end tell

using terms from application "Notifications Scripting"

  -- This handler is called when a notification was delivered.
	-- All parameters are optionnals.

	on notification delivered title aTitle subtitle aSubTitle message aMessage actual delivery date aDeliveryDate

    tell application "Finder"

			display dialog aTitle & return & aDeliveryDate

		end tell

	end notification delivered

	-- This handler is called when a notification was activated.
	-- All parameters are optionnals.

	on notification activated title aTitle subtitle aSubTitle message aMessage delivered date aDeliveryDate activation type aType

		tell application "Finder"	

			-- activation type describe how the user notification was activated :
			-- 1 : the user clicked on the contents of the notification alert
			-- 2 : the user clicked on the action button of the notification alert	
			-- 3 : the user replied to a notification
            -- 4 : the user clicked on the additional action button of the notification alert

			display dialog (aTitle & return & "activation type " & aType as text)

		end tell

	end notification activated

end using terms from
```

# History

v1.2 - Febrary 20, 2026
- Optimized for Apple Silicon.
- The application has been notarized.

v1.1 - March 5, 2014
- Added support for new notification features available in OS X Mavericks.
- Added a window that can show the event handler results for debugging purposes.
- Empty event handlers are not longer required if you only need to display a notification.
- The user info property has been removed.
- The application has been digitally signed for Gatekeeper.

v1.0 - September 21, 2012
- Initial release.

# Supported platforms
macOS

# System Requirements
Mac OS X v10.13 or higher.

# Languages available
English

# Icon Design
[Design Contest](https://www.designcontest.com/)

# License
Notifications Scripting is a donationware.

