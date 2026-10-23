# Handyman Board – Team Version Setup (about 20 minutes, one time)

This version lets you and every worker sign in on their own phone and see the same jobs.
Workers only see jobs assigned to them. You (the owner) see everything.

## 1. Create a free Firebase project
1. Go to https://console.firebase.google.com and sign in with a Google account.
2. Click **Create a project**, name it (for example "handyman-board"). You can turn Google Analytics off.

## 2. Turn on logins and the database
1. Left menu, **Build > Authentication > Get started > Email/Password > Enable > Save**.
2. Left menu, **Build > Firestore Database > Create database**. Pick the location closest to you.
   Choose **Production mode**, then Create.
3. In Firestore, open the **Rules** tab. Delete what is there, paste the entire contents of the
   file **firestore.rules** from this folder, and click **Publish**. This is what keeps workers out of
   other people's jobs and customer data. Do not skip it.

## 3. Copy your settings into the app
1. In Firebase click the gear icon > **Project settings**. Under "Your apps" click the **</>** (web) icon,
   give it any nickname, and click Register app.
2. You will see a block of code with apiKey, authDomain, projectId and so on.
3. Open **firebase-config.js** in this folder (Notepad is fine) and replace each "PASTE_..." value
   with the matching value from Firebase. Keep the quotation marks. Save the file.

## 4. Put it online
1. Go to https://app.netlify.com/drop and drag this whole folder onto the page. You get a web address.
2. Open that address on your phone. You should see the sign-in screen.

## 5. Create your owner account (only once)
1. Tap **First time? Create company**. Enter the company name, your name, email and a password.
2. Open the **Workers** tab, tap **+ New worker**, fill in their name, pay rate, and a login email and
   temporary password. Give them the address and their login. Each worker signs in on their own phone.
3. Assign jobs to workers (open a card > Assigned to). The worker sees it on their phone within seconds.

## 6. Make it an Android app (optional)
Go to https://www.pwabuilder.com, enter your Netlify address, then **Package for stores > Android >
Generate**. Install the APK on the phones, or upload the AAB to Google Play.

## Good to know
- Works offline; changes sync when the phone gets signal again.
- Workers can: see their jobs, call/text/map, use the timer, checklist and photos, move cards, take payment.
  Workers cannot: see other workers' jobs, customers list, pay rates, or edit/delete cards.
- To remove a worker, delete them in the Workers tab. This also removes their login profile.
  (Their sign-in email stays in Firebase > Authentication; you can delete it there too.)
- Card payment is still a preview only. Real card processing (Stripe or Square) is the next step.
- Firebase's free plan is plenty for a small crew. Photos are compressed to keep storage small.
