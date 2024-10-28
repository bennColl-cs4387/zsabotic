
# Investigation Log

### Step 1: Looked at the Reports

```bash
git checkout gtpd-archive
```

### Step 2: List Commits by Date

```bash
git log --graph --pretty=format:"%C(yellow)%h%x09%Creset%C(cyan)%C(bold)%ad%Creset %C(yellow)%cn%Creset  %C(green)%Creset %s" --date=default
```

### Step 3: Only Entry by Kyle That Day

```bash
git show 0e63b5b41dec7b308fce23b5bc2676b4300312f2
```

```
commit 0e63b5b41dec7b308fce23b5bc2676b4300312f2
Author: Kyle Pumbinner <kpumbinner@gtpd.gittown.gov>
Date:   Wed Jul 24 21:44:00 2019 +0000

    Crime scene report #956171
    
    Murder took place ten days ago, on July 14th. Coroner report says it was some time between 16:13 and 19:37.
    
    According to the security guard that sat at the entrance to the factory, on the day of the murder no one came through the front door. So that leaves the back door, which requires an RFID card to open.
    
    With the help of the factory's IT department, I managed to cherry-pick the relevant commits from the access log for all the electronically locked facilities on premise. They're on my personal 'detectives/kpumbinner' branch. But they said the program doesn't have a search button... I'll have to sift through it to find who used "BACKDOOR_332". I put the log file in the evidence folder to look through later.
```

---

### Step 4: Chose Cosmo First

```bash
git checkout detectives/kpumbinner
git log -p -S'BACKDOOR_332'
```

**Relevant Entries**:

- **Author**: Brock Stuickard <stuickard.brock@commitfactory.com>  
  **Date**: Sun Jul 14 15:23:00 2019 +0000  
  **Message**: ACCESS LOG COMMIT 15:23

- **Author**: Cosmo Siwkonk <siwkonk.cosmo@commitfactory.com>  
  **Date**: Sun Jul 14 14:16:00 2019 +0000  
  **Message**: ACCESS LOG COMMIT 14:16

- **Author**: Lyndon Huskupper <huskupper.lyndon@commitfactory.com>  
  **Date**: Sun Jul 14 12:06:00 2019 +0000  
  **Message**: ACCESS LOG COMMIT 12:06

---

### Step 5: Investigating Cosmo

```bash
git tag
git checkout street/balcombe_close
git log --grep="26 Balcombe Close"
```

```bash
git show c8411c73e49372dbdb644beef2ea841b403fc476
```

Cosmo wasn't there, but I found a **green Hyundai**.

---

### Step 6: Checking Other Suspects

```bash
git checkout street/beaconside
git log --grep="9 Beaconside"
```

**Brock** saw a green Hyundai. Checking the solution.

---

### Step 7: Confirming the Murderer

```bash
echo "Cosmo Siwkonk" | git hash-object --stdin | grep -iq -f /dev/stdin <(git show solution) && echo 'You found the murderer!' || echo 'No cigar, chief... Try again.'
```

**Result**: You found the murderer!
