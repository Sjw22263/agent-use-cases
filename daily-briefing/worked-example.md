# Worked example (fictional)

*Everything here is invented: the person, the businesses, the mail, the calendar and the addresses. It shows the workflow and a representative page. It is not output from a live run.*

## The setup

Jordan runs a small design studio. Their assistant runs at 7.00am every day and publishes the briefing to a private page Jordan has bookmarked on their phone and laptop. It reads two mailboxes (personal and studio) and one calendar, all read-only, and pings Jordan on a chat app when the page is up.

## Thursday 12 March: what the run finds

- **Personal mail:** OK, read to 6.58am. Contains a council rates notice (on direct debit, same amount as last quarter), a confirmation from Bayview Dental moving Jordan's check-up to Friday 9.30am, and an "Account suspended, verify now" email from a lookalike courier domain.
- **Studio mail:** unavailable. The connector reports that its sign-in has expired; Jordan changed the account's password yesterday.
- **Calendar:** OK. Friday 9.00 to 10.00am is already booked: a client workshop in the city.
- **Dates list:** domain name renewal due 20 March, not done.

## The judgement calls

- **The studio mailbox.** The tempting output is a clean page with no studio items. That would tell Jordan the studio was quiet when it wasn't checked. Instead the page shows the outage in the source strip and in place of the studio section, and "Reconnect studio mail" goes under Needs you. The studio read marker stays at Wednesday 6.58am.
- **The rates notice.** It's on direct debit and unchanged: Ignored, counted in the one line.
- **The dentist.** The confirmation reads as routine. Checked against the calendar, it clashes with the workshop. Needs you.
- **The courier email.** Lookalike domain, urgency, a "verify" link. Ignored, flagged as phishing with the reasons; the link isn't opened.
- **The domain renewal.** Inside its 14-day warning window for the first time, so it's reported today.

## The page as Jordan sees it

> **This briefing is current.** *(no banner showing)*
>
> # Briefing, Thursday 12 March
>
> Prepared 7.04am. Personal mail read to 6.58am.
>
> ✓ Personal mail: read to 6.58am
> ✗ Studio mail: unavailable (sign-in expired). Not checked today.
> ✓ Calendar: next 14 days
>
> ## Needs you
> - **Reconnect studio mail.** Its sign-in expired after yesterday's password change, so nothing from it is on this page. Once you've signed in again, tomorrow's briefing will cover everything since yesterday morning.
> - **Dentist clash.** Bayview Dental moved your check-up to Fri 9.30am, which is during the 9 to 10 client workshop. Ask them for another time, or move the workshop.
>
> ## Today and this week
> - Today: nothing booked.
> - Fri: client workshop, 9 to 10am, city (see clash above).
>
> ## Dates and waiting on
> - Studio domain renewal due Fri 20 March. Not done.
>
> ## Worth knowing
> - Nothing today.
>
> ## Ignored
> - 1 phishing email: "Account suspended", from a lookalike courier domain with an urgent verify link. Don't click it.
> - 1 rates notice (direct debit, same as last quarter), 7 newsletters, 2 receipts.

**The ping:** "Briefing ready: 2 things need you. Studio mail unavailable."

## Friday 13 March

Jordan reconnected the studio account on Thursday evening; the assistant didn't and couldn't, because signing in is Jordan's job. Friday's run reads studio mail from Wednesday 6.58am, because the marker was held, and finds a client's change request from Wednesday afternoon. It goes under Needs you, labelled "arrived Wed, missed yesterday while studio mail was down". Had the marker advanced on Thursday, that email would never have reached the page.

## If Saturday's run hadn't started at all

Say the machine running the scheduler was off. No run, no failure page, no ping. Jordan opens the bookmark at 8am and sees Friday's page with the banner across the top: "This is an old briefing. Today's run hasn't published." The page knows its own age, so the case the assistant can't report on is still visible.

## How the result would be verified

- The header date and the source strip are checked against the run log.
- The held marker is checked by confirming Friday's page included the Wednesday email.
- The staleness banner is tested by opening a copy whose prepared time is set two days back.
- Privacy: the page is opened with the browser's network panel showing that nothing loads beyond the page itself.

## What stays with Jordan

Signing in to the studio account. Replying to the dentist and the client. Paying for the domain renewal. The assistant prepares all three on the page; it does none of them.
