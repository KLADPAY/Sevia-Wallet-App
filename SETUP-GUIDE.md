# Opening the Sevia door — setup guide

You now have a visitor door and a keeper's list for the Sevia testnet wallet. They live in
your own Firebase project (`awuraba-frozen-foods`) and on your own GitHub Pages site.
Nothing here touches your frozen-foods records — the door keeps its guest list in a
separate drawer called `wd_visitors`.

**What you have**

| File | What it is | Where it goes |
|---|---|---|
| `index.html` | The door your visitors see | `wallet-fb/index.html` |
| `doorkeeper.html` | Your keeper's list (owner only) | `wallet-fb/doorkeeper.html` |
| `wallet-fb.html` | The wallet, behind the door | `wallet-fb/wallet-fb.html` |

All three must sit in the **same folder** on the website. Keep the file names exactly as
they are.

You need about 15 minutes, your phone, and the computer you use for the management page.

---

## Step 1 — Tell Firebase the door rules

Firebase has to know that strangers may knock, but only you may open the door.

1. Go to **console.firebase.google.com** and open the project **awuraba-frozen-foods**.
2. In the left menu choose **Firestore Database**, then the **Rules** tab at the top.
3. You will see a page of text. **Copy all of it into a note to yourself first.** That is
   your safety copy in case anything goes wrong.
4. Click at the very end of the text, just **before the last two `}` lines**, and press
   Enter to make a new line.
5. Open the file **`firestore.rules.snippet`**, copy everything in it, and paste it there.
6. Press **Publish**. Wait for the green "Rules published" note.

Then open your management page and check that your normal data still loads. If anything
looks wrong, paste your safety copy back into the Rules page and press Publish again —
nothing is lost.

> Not comfortable editing that text? Take a screenshot of the whole Rules page, send it to
> your agent, and ask for the complete file to paste in one go.

---

## Step 2 — Put the three pages online

Your site lives in the GitHub repository **seamihub.github.io**.

1. Go to **github.com/seamihub/seamihub.github.io**.
2. Click **Add file → Upload files**.
3. Drag the whole **`wallet-fb`** folder (the one holding the three files) onto the page.
4. Click **Commit changes** and wait a minute or two.

Your pages will be at:

- Door — `https://seamihub.github.io/wallet-fb/`
- Keeper's list — `https://seamihub.github.io/wallet-fb/doorkeeper.html`
- Wallet — `https://seamihub.github.io/wallet-fb/wallet-fb.html`

If the folder will not drag, make it by hand: **Add file → Create new file**, type
`wallet-fb/README.md` as the name, commit, open the new folder, then **Add file → Upload
files** and drop the three files inside it.

---

## Step 3 — Let your phone ring

The phone nudge uses a free app called **ntfy**. No account needed.

1. Install **ntfy** from the App Store or Play Store.
2. Open it, tap **+**, choose **Subscribe to topic**, and type:

   ```
   sevia-door-83e8999caf3d28f8c6eaf383
   ```

3. Send yourself one test message from the app to be sure notifications are allowed.
4. On Android, also open the phone's settings for ntfy and allow **background activity**,
   otherwise the ring may wait until you open the app.

You can copy that topic from the bottom of your keeper's list page (there is a **Copy
topic** button).

---

## Step 4 — Open your keeper's list

1. Go to `https://seamihub.github.io/wallet-fb/doorkeeper.html`.
2. Tap **Sign in with Google** and choose **seamihub@gmail.com**.

The list only opens for that address. Any other account sees a polite refusal.

**If Google sign-in complains**, two one-time switches in the Firebase console fix it:

- **Authentication → Sign-in method → Google → Enable** (if it is off).
- **Authentication → Settings → Authorized domains → Add domain → `seamihub.github.io`.**

Until then you can use **"Use email and password instead"** with the same login you use for
the management page — that already works.

---

## Step 5 — Try it once, properly

Use your phone for the visitor side and your computer for the keeper side.

1. On your phone, open `https://seamihub.github.io/wallet-fb/`.
2. Type a name, tick the feedback promise, and tap **Introduce myself**. Your phone should
   ring with "Someone is at the Sevia door".
3. On the computer, the keeper's list shows the visitor with a 📗 badge. Tap **Let in**.
4. Within a few seconds the phone opens the wallet by itself.

That is the whole flow. Share the door link with the people you want to test the wallet.

---

## Day to day

- **Let in** opens the wallet for that visitor. **Shut out** shows them "Not available right
  now." **Waiting room** puts them back to waiting.
- The list refreshes itself; you can leave it open on a tab.
- "Opened 4 times" counts how many times that visitor loaded the door — a good sign of real
  interest.
- Names are whatever people typed. If someone types nothing you will see `Visitor a1b2c3…`.

---

## If something looks wrong

| What you see | What it means |
|---|---|
| Door says **"The door is slow to answer — retrying…"** | The rules in Step 1 are not published yet, or the visitor has no internet. |
| Keeper's list says **"The list could not load"** | Same cause: Step 1. Publish the rules, wait a minute, refresh. |
| Wallet says **"Not available right now."** | That visitor is blocked, or opened an old link. Go through the door again. |
| No ring on the phone | Check the topic is exactly `sevia-door-83e8999caf3d28f8c6eaf383`, and allow background activity for ntfy. |
| Google sign-in window never opens | Allow pop-ups for the page, or use email and password. |

---

## One honest note

The cover on the wallet page is a **friendly door, not a vault**. It hides the wallet from
ordinary visitors and only opens for people you approved, but someone technical could get
past it. That is fine for a testnet with practice coins — just never put real money behind
it. The wallet's own PIN and backup words still protect the coins themselves.
