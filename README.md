# Amex Offers Auto-Save Script

This repository contains a JavaScript snippet to automate saving all **Amex Offers** to your card. The script uses `querySelectorAll` to find buttons labeled **"Save to Card"** and simulates real clicks with `MouseEvent`.

## How It Works
1. Finds all "Save to Card" buttons on the page.
2. Loops through each button and simulates a user click.
3. Adds a delay (1.5 seconds) between clicks to ensure smooth interaction.

## Usage
1. Open the [Amex Offers](https://global.americanexpress.com/offers/eligible) page in your browser.
2. Open the developer console:
   - Right-click anywhere on the page and select **Inspect**.
   - Go to the **Console** tab.
3. Copy and paste the script into the console, then hit **Enter**.
4. The script will click through all "Save to Card" buttons for you.

## Script
```javascript
(async () => {
    const offerButtons = Array.from(document.querySelectorAll('button, a'))
        .filter(el => el.textContent.trim() === "Save to Card");

    console.log(`Found ${offerButtons.length} buttons to click`);

    for (let index = 0; index < offerButtons.length; index++) {
        console.log(`Clicking button ${index + 1} of ${offerButtons.length}`);
        offerButtons[index].dispatchEvent(new MouseEvent('click', { 
            bubbles: true, 
            cancelable: true, 
            view: window 
        }));
        await new Promise(r => setTimeout(r, 1500));
    }

    console.log("All offers should now be saved to your card!");
})();
```

## Disclaimer
* This script is provided for educational purposes. Use it responsibly and at your own risk.
* Ensure you comply with Amex’s terms of service when using this tool.

## The Ironic Note

Now, the irony is that it’s probably quicker to click through all the buttons manually than to write or use this script. 😊
