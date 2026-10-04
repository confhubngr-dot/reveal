# Reveal by ConfHub: launch and monetisation guide

> **Update 2.** The export mark reads "Reveal by ConfHub" and tapping it in the studio opens https://reveal.confhub.ng. The studio follows each visitor's device theme, with a light/dark toggle. Background music is generated in the browser. To offer your own licensed tracks, put MP3 files in a `music` folder next to `index.html` and list them in `tracks:[{name:'My track',file:'music/my-track.mp3'}]` inside `CFG`.
> **Traffic:** if the site is on Cloudflare, switch on Web Analytics in the dashboard and paste its snippet where the page says "Analytics". Plausible or Umami also work and add custom events: this page already reports export, waitlist, logo, music and mark_click when one of them is installed.
> **Ads:** do not add display ads yet. See the chat notes.
> **New tools:** 4:5, 9:16 and 1:1 sizes, animated reveal slider, captions, closing "Book now" card, brand kit saved on the visitor's device, video trimming, frames and 5 templates.
>
> **Update: launched free.** Everyone can use Reveal for free with the small "Made with confhub.ng" mark. The Pro code box is hidden. Visitors who want the mark gone join a waitlist that emails hello@confhub.ng.
> - To receive waitlist signups silently, create a free form on Formspree, Web3Forms or similar, paste its endpoint into `formUrl:''` in `index.html`, and switch on its auto-reply. Without it, the button opens the visitor's email app with the message ready to send.
> - Make sure hello@confhub.ng really receives mail (for example with Cloudflare Email Routing).
> - To turn Pro on later, set `showPro:true` and follow sections 4 to 7 below.


## 1. What to call it
Recommended: **Reveal** (tagline: "Before & after posts, ready for Instagram"), hosted at **reveal.confhub.ng**. It is short, easy to say and describes the before-and-after moment.
Other options: Glow Reveal, Transform Studio, BeforeAfter Studio, PostReveal. Check the Instagram handle and domain are free before you settle.

## 2. Put it online at reveal.confhub.ng
1. Use a free host such as Cloudflare Pages or Netlify. Create a project and upload the `index.html` from this zip (drag and drop works on both).
2. In the host's settings, add the custom domain `reveal.confhub.ng`.
3. At wherever confhub.ng's DNS is managed, add a CNAME record for `reveal` pointing to the address the host gives you. HTTPS is issued automatically. DNS can take minutes to a few hours.
4. Open the site on a phone and a computer and test an export before you tell anyone.

## 3. Who to sell to
Aesthetic and skin clinics, dental clinics, hair stylists and braiders, barbers, makeup artists, lash and nail techs, fitness coaches, cleaners, painters and renovators, car detailers. Face blur is the selling point for clinics that worry about patient privacy.

## 4. Pricing to test (starting points, not facts)
- **Free:** every feature, small "Made with confhub.ng" mark on exports. This is your marketing.
- **Pro:** removes the mark. Try about N2,500 per month, N20,000 per year, or a one-off N8,000.
- **Teams:** 5 codes for a clinic with several staff.
- **Done-for-you:** you make their first 5 posts for a fee. Good for early cash and for learning what customers want.
Ask 10 real prospects what they would pay before you fix a price.

## 5. Taking payment today with no coding
1. Open a Paystack (or Flutterwave) account and create a payment page for "Reveal Pro". Check their current fees and payout times.
2. Paste the page link into `payUrl:''` near the top of the script in `index.html`. A "Get a Pro code" button then appears.
3. When someone pays, send them one unused code from the list below by WhatsApp or email.
4. Keep a simple sheet: code, customer, date, plan.

## 6. How the codes work, and the limits
The page stores only SHA-256 hashes of valid codes, so the codes are not readable in the source. Everything runs in the visitor's browser, so a technical person can still bypass it. That is fine at the start, because people who would bypass it were never going to pay.
When you have steady sales, add a small serverless function (Cloudflare Workers or Netlify Functions) that checks Paystack webhooks, issues codes, expires them and limits devices.

To add more codes, run this in your browser console (F12) for each new code, then paste the result into `hashes:[...]` in `index.html`:

    const h=async s=>[...new Uint8Array(await crypto.subtle.digest('SHA-256',new TextEncoder().encode(s.trim().toUpperCase())))].map(x=>x.toString(16).padStart(2,'0')).join('');
    await h('RV-ABCD-2345')

## 7. Your starter codes (keep private)
- RV-3B6Q-4VYN
- RV-ND3H-AW9N
- RV-4XPT-M3NM
- RV-7KVD-6ZUS
- RV-6ARN-3FMT
- RV-EHTR-77MN
- RV-46ND-8M7Q
- RV-TTJC-3BQN
- RV-J3ZU-K7FR
- RV-63ZE-CXBW

## 8. Getting your first customers
- Use the tool for your own clinic and post the results. The free mark advertises it every time.
- Offer 3 free months to 10 businesses in return for a testimonial and a tag.
- Share short screen recordings on Instagram, TikTok and WhatsApp status showing a blurred before-and-after made in under two minutes.
- Pay 20% of the first payment to beauty-school, clinic and influencer partners who send buyers.
- Write simple pages for searches like "before and after video maker" and "blur face in video".
- Add privacy-friendly analytics (Cloudflare Web Analytics or Plausible) so you can see where visitors drop off.

## 9. Trust and legal
- Add short Terms and Privacy pages: files are processed on the device, the logo and Pro code are stored in the browser, there is no refund after a code is used, and users are responsible for consent.
- Health images are sensitive personal information under Nigeria's data protection law. Get proper legal advice before you target clinics. This guide is not legal advice.

## 10. Next features worth building
Because it will now be on your own domain, you can host face-detection model files yourself, which allows automatic face finding and AI background removal that the preview version cannot do. Also worth adding: templates and frames, captions, batch export, saved brand kits and accounts with subscriptions.
