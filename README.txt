V18 - Abdelrahman Website

Same Firebase system as V17.

Fixes:
- Admin button/login flow made more reliable and opens the dashboard after successful Firebase Auth.
- Dashboard opens before rendering its tabs so a rendering error does not make the whole dashboard appear unresponsive.
- Gallery uploads are processed in small parallel batches (4 at a time) instead of one-by-one, reducing long waits.
- Uploads require the authenticated admin session.
- Firebase Storage and Firestore remain the same system; no Cloudinary was added.

Important:
Firebase Storage must be enabled/available in the Firebase project for image uploads. If Firebase shows an Upgrade/Billing requirement for Storage, code changes cannot bypass that service requirement.

Deploy:
Upload index.html and rules files as usual. If rules were changed, publish firestore.rules and storage.rules in Firebase.


V19 hotfix:
- Firebase Storage is now initialized lazily, so a project that has not enabled Storage does not prevent the rest of the site/admin login from starting.
- The admin icon has a fallback click handler, so the login modal can still open if another startup component fails.
- Existing Firebase Auth/Firestore system and admin email remain unchanged.
