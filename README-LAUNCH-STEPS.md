# Sky Stack - Launch Steps (no computer needed)

Everything here works from your iPhone/Android browser.

## STEP 1 - Put this project on GitHub (10 min)
1. Create free account at github.com (use lletmonk@gmail.com)
2. New repository -> name: sky-stack -> Private -> Create
3. On the repo page: "uploading an existing file" -> upload ALL files
   from this package KEEPING the folder structure:
   - capacitor.config.json, package.json, codemagic.yaml (root)
   - www/index.html
   - assets/ (all 5 png files)
4. Commit changes.

## STEP 2 - Connect Codemagic (10 min)
1. Sign up free at codemagic.io with your GitHub account
2. Add application -> select sky-stack repo -> "Codemagic YAML" detected

## STEP 3 - Create your signing key ONCE (5 min)
1. Start new build -> workflow: "1 - Generate signing keystore"
2. When it finishes, DOWNLOAD both artifacts:
   - keystore.jks
   - keystore-info.txt (contains your password)
3. SAVE BOTH to Google Drive. If you ever lose the keystore,
   you can never update the app again. Guard it like a passport.
4. In Codemagic: your app -> Environment variables -> add group "signing":
   - CM_KEYSTORE_PASSWORD = the password from keystore-info.txt
   - CM_KEY_ALIAS = skystack
   Then Teams/App settings -> Code signing -> upload keystore.jks
   (or add CM_KEYSTORE as a secure FILE variable in group "signing")

## STEP 4 - Build the app (15 min, automatic)
1. Start new build -> workflow: "2 - Build Sky Stack AAB"
2. Download the artifact: app-release.aab
   (Save it to your phone / Google Drive)

## STEP 5 - Create the app in Play Console
1. play.google.com/console -> Create app
   - Name: Sky Stack | Default language: English
   - App or game: GAME | Free
2. Complete "Set up your app" checklist using store-assets/store-listing.md:
   - Privacy policy URL: (host privacy-policy.html - see Step 6)
   - App access: All functionality available without login
   - Ads: NO | Content rating: fill questionnaire (answers in listing file)
   - Target audience: 13+ (simplest; do NOT tick "appeals to children"
     unless you want the stricter Families policy)
   - Data safety: does NOT collect or share data
   - Store listing: paste descriptions, upload icon-512, feature graphic,
     both screenshots (add 2 real screenshots from your phone later)

## STEP 6 - Host the privacy policy (5 min)
Easiest: GitHub Pages
1. In your sky-stack repo -> Settings -> Pages -> Deploy from branch: main
2. Your policy will be at:
   https://YOURUSERNAME.github.io/sky-stack/privacy-policy.html
3. Paste that URL into Play Console -> Privacy policy

## STEP 7 - Upload + closed testing
1. Play Console -> Testing -> Closed testing -> Create track "beta"
2. Create release -> upload app-release.aab -> release notes from listing file
3. Testers tab -> create email list -> add 12-15 Gmail addresses
   (or order the Fiverr 12-tester service NOW and give them the link)
4. Copy the opt-in link -> send to testers -> they tap "Become a tester"
   and install
5. Keep 12+ opted in for 14 continuous days

## STEP 8 - Go live
Dashboard -> "Apply for production access" -> answer the questionnaire
-> once approved -> Production -> Create release -> upload same .aab
-> submit for review -> LIVE.

Questions at any step: just ask Claude and paste a screenshot.
