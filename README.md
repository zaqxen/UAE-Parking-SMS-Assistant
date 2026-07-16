# UAE Parking SMS Assistant

A compact, mobile-first web page that helps drivers generate correctly formatted UAE parking SMS messages.

The user selects the parking emirate, chooses the parking system or area when required, enters the vehicle plate details, previews the generated SMS, and opens the phone's messaging application with the shortcode and message body already populated.

**Author:** Zaqxen

---

## Features

- Mobile-first interface designed for small screens such as the iPhone SE.
- Large, legible text for easier use at arm's length.
- Tap-based emirate and parking-system selection.
- Dynamically shows only the fields required for the selected parking system.
- Live preview of:
  - SMS shortcode
  - SMS message body
- Opens the mobile messaging application using an `sms:` link.
- Copies the generated shortcode and message to the clipboard.
- Saves vehicle plate details in browser `localStorage`.
- Automatically restores previously saved vehicle details.
- Supports light and dark device themes.
- No frameworks, libraries, APIs, or backend server required.
- All HTML, CSS, and JavaScript are contained in one file.

---

## Supported Parking Systems

| Parking Location | System | Shortcode | Generated Format |
|---|---|---:|---|
| Dubai | RTA / Parkin | `7275` | Dubai plate: `<PlateCode><PlateNumber> <Zone> <Hours>` |
| Dubai | RTA / Parkin | `7275` | Other emirate: `<Emirate><PlateCode> <PlateNumber> <Zone> <Hours>` |
| Dubai | Parkonic | `6670` | `<Emirate><PlateCode> <PlateNumber> <ParkonicZone> <Hours>` |
| Abu Dhabi | Mawaqif | `3009` | `<Emirate><PlateCode> <PlateNumber> <Type> <Hours>` |
| Sharjah | Sharjah City | `5566` | `<Emirate> <PlateNumber> <Hours>` |
| Sharjah | Khorfakkan | `5566` | `<Emirate> <PlateNumber> KH <Hours>` |
| Ajman | Ajman Public Parking | `5155` | `<Emirate> <PlateCode> <PlateNumber>` |

> Parking formats and shortcodes may change. Always compare the generated message with the instructions printed on the parking sign before sending.

---

## Parkonic Zones Included

| Code | Area |
|---|---|
| `P100` | Dubai Harbour |
| `P101` | Golden Mile |
| `P102` | Galleria Mall |
| `P103` | Global Village |
| `P104` | Nad Al Hamar |
| `P105` | JVC |
| `P106` | Discovery Gardens |
| `P107` | Dubai Silicon Oasis |
| `P108` | Palm Crescent |
| `P109` | Peninsula Five |
| `P110` | Tilal Al Ghaf |

A custom Parkonic zone can also be entered when the zone printed on the parking sign is not included in the list.

---

## Example

For a Dubai vehicle with:

- Plate code: `EE`
- Plate number: `58378`
- Parkonic zone: `P105`
- Duration: `2` hours

The application generates:

```text
Shortcode: 6670
Message: DXBEE 58378 P105 2
```

For the same vehicle using Dubai RTA parking in zone `335A` for two hours:

```text
Shortcode: 7275
Message: EE58378 335A 2
```

---

## How to Use

1. Open `index.html` on a mobile device.
2. Tap the emirate where the vehicle is being parked.
3. Select the parking system or area when more than one option is available.
4. Select the emirate where the vehicle plate was issued.
5. Enter the plate code and plate number.
6. Select the zone, parking type, and duration when required.
7. Review the shortcode and SMS body in the preview.
8. Tap **Open SMS App**.
9. Confirm the message details before sending.

---

## Installation

No installation or build process is required.

Clone the repository:

```bash
git clone <your-repository-url>
cd <your-repository-folder>
```

Open the file directly:

```text
index.html
```

The page can also be hosted using:

- GitHub Pages
- Netlify
- Vercel
- Cloudflare Pages
- Any standard web server

---

## GitHub Pages Deployment

1. Push `index.html` to the repository.
2. Open the repository on GitHub.
3. Go to **Settings**.
4. Select **Pages**.
5. Under **Build and deployment**, choose **Deploy from a branch**.
6. Select the branch containing `index.html`.
7. Select the root folder.
8. Save the configuration.

GitHub will provide a public URL after deployment.

---

## Project Structure

```text
.
├── index.html
└── README.md
```

The complete application is contained in `index.html`.

---

## Local Storage

When **Remember plate** is enabled, the following details are stored in the browser:

- Plate emirate
- Plate code
- Plate number

The information remains on the user's device and is not transmitted to a server.

The saved information can be removed by tapping **Clear saved**.

---

## Privacy

This application:

- Does not require user registration.
- Does not use analytics.
- Does not use cookies.
- Does not send plate information to a server.
- Does not communicate with a third-party API.
- Stores optional vehicle information only in the user's browser.

The final SMS is handled by the mobile device's messaging application and telecommunications provider.

---

## Mobile SMS Compatibility

The page generates an `sms:` URI containing:

- The parking shortcode as the recipient.
- The generated parking message as the SMS body.

Mobile operating systems may handle SMS links differently. The application includes handling for common iOS and Android URI formats.

Desktop browsers may not have an SMS application registered and may therefore be unable to open the generated link.

---

## Browser Support

The application is intended for modern mobile browsers, including:

- Safari on iOS
- Google Chrome on Android
- Samsung Internet
- Microsoft Edge
- Other modern Chromium-based browsers

Clipboard access may require HTTPS when the page is hosted online. A fallback copy method is included for browsers where the Clipboard API is unavailable.

---

## Customization

All parking configuration and interface logic are contained inside `index.html`.

The main configuration objects are:

```javascript
const systems = {
  // Parking systems grouped by emirate
};
```

```javascript
const parkonicZones = [
  // Parkonic zone codes and area names
];
```

To add a new parking system:

1. Add it to the `systems` object.
2. Add its dynamic fields in `renderSystemFields()`.
3. Add its SMS format in `getMessageData()`.
4. Test the generated shortcode and body on both iOS and Android.

---

## Safety Notice

This project assists with formatting parking SMS messages but does not verify that:

- A parking zone is currently active.
- The selected duration is permitted.
- The parking operator has changed its shortcode.
- The parking fee was successfully charged.
- The telecommunications provider delivered the SMS.
- A confirmation message was received.

The driver remains responsible for checking the parking sign and waiting for a successful confirmation SMS.

---

## Contributing

Contributions are welcome.

Suggested improvements include:

- Additional UAE parking operators.
- Updated parking zones.
- Arabic interface support.
- Saved multiple vehicle profiles.
- Installable Progressive Web App support.
- Offline application caching.
- Accessibility testing across more devices.

When submitting changes, include the source used to verify any new shortcode or message format.

---

## Author

Created by **Zaqxen**.
