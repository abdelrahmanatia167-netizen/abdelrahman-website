V14 WEBSITE UPDATE — FIRESTORE-ONLY PORTFOLIO UPLOAD

This package preserves the existing V14 design and includes:
- Local Arabic/English dictionary translation (no Google Translate widget).
- Lightweight click micro-interactions and animations.
- Separate portfolio galleries by category.
- Portfolio cover/gallery image upload saved as compressed image data in Firestore.
- Customer email/password authentication separated from the admin login entry.
- Admin review and chat management tools already present in this V14 build.

IMPORTANT: This version does NOT require Firebase Storage for portfolio images.
Images are resized/compressed in the browser and stored as separate documents in the Firestore `projectImages` collection. Each image is kept below the Firestore document size limit. This is suitable for a modest portfolio; storing very large galleries this way can increase Firestore storage and read costs. Firebase Storage remains the better long-term choice for hundreds of large images.

PUBLISH FIRESTORE RULES:
1. Open Firebase Console and choose project `abdelrahman-website-98d4c`.
2. Open Firestore Database > Rules.
3. Back up the existing rules, replace them with the contents of `firestore.rules`, and click Publish.
4. Do NOT publish `storage.rules`; it is not required by this build.

GITHUB PAGES DEPLOY:
1. Extract this ZIP.
2. Upload `index.html`, `1001809140.jpg`, `1001778764.jpg`, and `README.txt` to the root of the existing GitHub repository.
3. `firestore.rules` is for Firebase Console only; it does not automatically publish when uploaded to GitHub.
4. After GitHub Pages finishes deploying, hard-refresh the website and test admin login, saving text, and uploading one small image first.

ADMIN AUTH:
The admin email configured in the code/rules is `abdelrahmanatia167@gmail.com`. This email must exist as a user in Firebase Authentication, and Firestore must be enabled in the same Firebase project.

LIMITATIONS:
- Firestore rules do not create or reset Firebase Authentication accounts.
- Client accounts use Firebase Authentication email/password.
- Image uploads should be tested with a few small files before selecting many images. Each compressed image is stored as a separate Firestore document.
