# Umm al-Qura Hijri calendar: month starts and key Islamic dates, 1447 to 1452 AH

The first day of every Hijri month from Muharram 1447 to Dhu al-Hijjah 1452 (June 2025 to April 2031) with its Gregorian date and the length of the month, by the Umm al-Qura calendar of Saudi Arabia. A second table and a calendar file list the six dates people ask for most: Islamic New Year, Ashura, the start of Ramadan, Eid al-Fitr, the Day of Arafah and Eid al-Adha.

Put together by the [HijriLive](https://hijrilive.com/en/hijri-calendar/) team. The live site has a [Hijri calendar](https://hijrilive.com/en/hijri-calendar/) for the current year, a [date converter](https://hijrilive.com/en/date-converter/) and a [Ramadan countdown](https://hijrilive.com/en/ramadan-countdown/).

## Files

| File | What it is |
|---|---|
| `data/hijri-months.csv` | 72 rows, one per Hijri month: year, month number, name in English and Arabic, Gregorian start date, weekday, days in the month |
| `data/islamic-dates.csv` | 36 rows: six key dates for each Hijri year from 1447 to 1452 |
| `data/hijri-calendar.json` | both tables in one file, with the source and licence fields |
| `islamic-dates.ics` | the 36 key dates as all-day events for Google Calendar, Apple Calendar or Outlook |

## Key dates (Gregorian)

| Hijri year | Start of Ramadan | Eid al-Fitr | Day of Arafah | Eid al-Adha |
|---|---|---|---|---|
| 1447 | 18 Feb 2026 | 20 Mar 2026 | 26 May 2026 | 27 May 2026 |
| 1448 | 8 Feb 2027 | 9 Mar 2027 | 15 May 2027 | 16 May 2027 |
| 1449 | 28 Jan 2028 | 26 Feb 2028 | 4 May 2028 | 5 May 2028 |
| 1450 | 16 Jan 2029 | 14 Feb 2029 | 23 Apr 2029 | 24 Apr 2029 |
| 1451 | 5 Jan 2030 | 4 Feb 2030 | 12 Apr 2030 | 13 Apr 2030 |
| 1452 | 26 Dec 2030 | 24 Jan 2031 | 1 Apr 2031 | 2 Apr 2031 |

## Quick use

Raw CSV:

```
https://raw.githubusercontent.com/RB9744/hijri-calendar-umm-al-qura/main/data/hijri-months.csv
```

Python:

```python
import csv, urllib.request
url = 'https://raw.githubusercontent.com/RB9744/hijri-calendar-umm-al-qura/main/data/islamic-dates.csv'
rows = list(csv.DictReader(urllib.request.urlopen(url).read().decode('utf-8').splitlines()))
print([r['gregorian_date'] for r in rows if r['event'] == 'Start of Ramadan'])
```

JavaScript:

```js
const r = await fetch('https://raw.githubusercontent.com/RB9744/hijri-calendar-umm-al-qura/main/data/hijri-calendar.json');
const cal = await r.json();
const ramadan1448 = cal.months.find(m => m.hijri_year === 1448 && m.hijri_month === 9);
// { gregorian_start: '2027-02-08', weekday: 'Monday', days: 29, ... }
```

## Where the dates come from

- Source: the official Umm al-Qura calendar, [ummulqura.org.sa](https://www.ummulqura.org.sa/). We read all six Hijri years from it on 16 November 2026.
- Second check: the `islamic-umalqura` calendar in Unicode ICU 78 (the one behind `Intl.DateTimeFormat` in browsers and Node). All 72 month starts and all month lengths are the same in both.

## Please read before you use it

- These are calendar dates. Saudi Arabia confirms the start of Ramadan, Shawwal and Dhu al-Hijjah by moon sighting, so the real day of Ramadan, Eid or Arafah can be one day away from this table. Many other countries follow their own sighting and can differ too.
- A Hijri day begins at sunset. The night of 1 Ramadan, for example, is the evening before the Gregorian date shown here.
- Month names in English are transliterations. Other spellings are just as common.

## Licence and credit

[CC BY 4.0](LICENSE). Please credit: "Hijri calendar data, HijriLive (https://hijrilive.com), from the Umm al-Qura calendar".

Found a mistake? Open an issue or write to assalamoalaikum@hijrilive.com.
