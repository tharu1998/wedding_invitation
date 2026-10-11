# Tharaka & Himaya — Royal Gold Wedding Invitation

A mobile-first, bilingual (English/Sinhala) wedding invitation site for **18 November 2026** at **Peradeniya Royal Rest House, Sri Lanka**.

## Included

- Animated invitation envelope and wax seal
- Royal gold / dark cinematic styling, subtle 3D particle background
- Live countdown to 18 Nov 2026 (noon Sri Lanka time placeholder until ceremony time is confirmed)
- English / Sinhala text toggle
- Optional background music button
- Couple story/photo placeholder
- Gallery with fullscreen lightbox (sample images are illustrative; replace with your own)
- Google Maps search link for the venue
- Downloadable calendar event
- Personalized guest links: `?guest=Guest%20Name` or `?to=Guest%20Name`
- RSVP form
- Admin dashboard with CSV export
- Optional Firebase / Firestore integration for online RSVPs
- GitHub Actions workflow to publish to GitHub Pages

## Publish to GitHub Pages

1. Create a new GitHub repository, for example `tharaka-himaya-wedding`.
2. Upload all files and folders in this package to the repository root. Include the hidden `.github` folder.
3. In the repository, open **Settings → Pages** and set **Build and deployment → Source** to **GitHub Actions**.
4. Push/commit to the `main` branch. The included workflow deploys the static site. Check the **Actions** tab for status.
5. Your site URL will look like `https://YOUR-USERNAME.github.io/tharaka-himaya-wedding/`.

Official GitHub Pages guidance: https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages

## Important: enable real online RSVP (Firebase)

GitHub Pages hosts static files. It does not itself provide a database or private admin authentication. The included RSVP works in **local demo mode** until Firebase is configured; local demo entries are saved only in the current browser and are NOT sent to the couple.

1. Create a Firebase project at https://console.firebase.google.com/
2. Add a Web App and copy its config into `assets/firebase-config.js`.
3. In Firebase Authentication → Sign-in method, enable **Email/Password**. Create an account for the admin email you control.
4. In Firestore Database, create a database.
5. Replace `YOUR_ADMIN_EMAIL@example.com` in BOTH `assets/firebase-config.js` and `firestore.rules` with the exact admin email.
6. Publish the contents of `firestore.rules` in Firebase Console → Firestore Database → Rules.
7. Deploy the website again. Test an RSVP from a different device and sign in at `/admin.html`.

**Security:** Never set Firestore rules to allow everyone to read/write all data. The provided rules allow public RSVP creation with validation, while only the configured admin email can read/update/delete RSVPs. Review rules before using in production. Firebase config's web API key is not a server secret; access control comes from Authentication and Security Rules.

Firebase docs:
- https://firebase.google.com/docs/firestore/security/get-started
- https://firebase.google.com/docs/auth/web/password-auth

## Add your own photos

- Add `assets/couple.jpg` and then replace the story placeholder in `index.html` with an image element pointing to `./assets/couple.jpg`.
- Replace the three sample gallery image URLs in `index.html` with your own uploaded files, for example `./assets/gallery-1.jpg`, etc.
- Use photos you have permission to publish. Sample images are illustrative stock photography.

## Add background music

Add a licensed/owned MP3 file named `assets/wedding-music.mp3`. Browsers require a tap before music can start, so guests control playback using the music button. The file is not included.

## Confirm before the wedding

- Ceremony start/end times are not yet supplied. The countdown uses noon Sri Lanka time as a placeholder; update `2026-11-18T12:00:00+05:30` in `assets/app.js`.
- Calendar event uses a placeholder time window; update the `DTSTART` and `DTEND` values in `assets/app.js`.
- Confirm the exact venue location and pin. The current Google Maps link searches the venue name.
- Update the sample gallery photos and couple photo.
- Replace the admin email in both config and Firestore rules.
- Consider a custom domain if desired.

## Personalized invitations

Share a link such as:
`https://YOUR-USERNAME.github.io/tharaka-himaya-wedding/?guest=Amali%20Perera`

The guest name appears as a welcome note and is prefilled in the RSVP form. This is a convenience feature, not private access control—anyone can edit a URL parameter.


## Personal photos and video added
- `assets/media/couple-main.jpg` is the couple photo provided by the couple.
- `assets/media/couple-video.mp4` is the third video uploaded in the conversation.
- `assets/media/gallery-01.jpg` through `gallery-04.jpg` are four crops from a generated wedding-style collage for the gallery. Replace these later with original photos if preferred.
- Keep the `assets/media` folder when uploading the updated website to GitHub.
