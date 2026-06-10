# Defect Log: ApexBank Mobile App

### [BUG-001] [Blocker] Wallet allows negative balance during P2P transfers
* **Severity:** Blocker (Financial/Data Integrity Loss)
* **Priority:** High
* **Environment:** Android 14 (Samsung S23) & iOS 17 (iPhone 14)
* **Steps to Reproduce:**
  1. Login with an account having a balance of 200 EGP.
  2. Go to E-Wallet Transfer.
  3. Enter recipient wallet ID and input amount: 500 EGP.
  4. Click "Confirm Transfer".
* **Expected Result:** Application blocks the request, raising an "Insufficient Funds" validation error.
* **Actual Result:** Transaction passes. The sender's balance updates to `-300 EGP`, allowing illegal overdraft.
* **Attachment:** `screenshot_neg_balance.png`

---

### [BUG-002] [Major] App crashes completely upon OS Low Battery Alert (20%) during data fetch
* **Severity:** Major (Crash / Functional Disruption)
* **Priority:** Medium
* **Steps to Reproduce:**
  1. Open App -> Go to Transaction History.
  2. While the loading spinner is active, simulate OS 20% Low Battery Warning notification.
* **Expected Result:** OS alert shows up, app stays alive in the background and finishes loading data.
* **Actual Result:** App process terminates instantly with a NullPointerException error in logs.
