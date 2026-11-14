# Nfc-fix-back-min-android-4.4  Send links and files between Android phones over NFC, like the old Android Beam. Works on Android 4.4+ with the app installed on both phones.# NFC Beam

Send links and files between two Android phones by touching their backs together, a bit like the old Android Beam. Install the app on both phones, tap **Receive** on one and **Send** on the other, then touch them together.

> Experimental hobby project. It works best with small files and may not work on every phone.

## What it does

- Sends a file (up to 5 MB) or a link from one phone to another over NFC
- Shows up in Android's Share menu, so you can share a link from Chrome or YouTube, or a photo from Gallery, straight to NFC Beam
- Pulsing-rings "beam" animation while it waits for the other phone
- Receiver gets a prompt to **Save**, **Open** (links), **Copy**, or **Discard**
- Keeps the screen on while sending or receiving
- Resumes where it left off if the phones slip apart mid-transfer
- No internet, accounts, or Bluetooth needed

## How to use it

1. Install the APK on both phones.
2. Make sure NFC is turned on in both phones' settings.
3. On the receiving phone, open NFC Beam and tap **Receive**.
4. On the sending phone, tap **Send a file**, or share something from another app and pick **NFC Beam**.
5. Touch the backs of the phones together and keep them still until it finishes.
6. On the receiving phone, tap **Save**. Files go to the Downloads folder.

## Requirements

- Android 4.4 (KitKat) or newer on both phones
- An NFC chip on both phones
- The receiving phone must support NFC card emulation (most NFC phones do)
- Both phones need the app open, with the screen on and unlocked

## Limitations

- **It's slow.** All data travels over NFC, roughly 5 to 20 KB per second. A 1 MB photo can take a minute or two, and you have to hold the phones still.
- **5 MB limit** per transfer.
- **Android to Android only.** Other devices, including iPhones, iPods, and anything without NFC, can't take part.
- **Screen must be on.** Android doesn't let apps send or receive NFC with the screen off or locked.
- **No Bluetooth speed-up yet.** Android 6 and later hide a phone's Bluetooth address from apps, so NFC can't hand it over to start a faster link.
- Not affiliated with Google, Samsung, or Apple. This is not the original Android Beam, which was removed from Android.

## Download

Get the latest APK from the **Releases** page on the right side of this repo. Tap `nfc-beam.apk` to download it, then allow "Install unknown apps" for your browser when Android asks.

The APK is a debug build, signed with a debug key, so Android or Play Protect may show a warning. It never asks for any permission except NFC.

## Build it yourself

You don't need a computer. The repo builds the APK in the cloud:

1. Upload `nfc-beam.zip` to the top folder of the repo.
2. Add the build recipe at `.github/workflows/build.yml`.
3. Open the **Actions** tab. The build runs on every upload, or tap **Run workflow** to run it by hand.
4. When it finishes, the new APK appears under **Releases**.

Or open the project in Android Studio and press Run.

## Under the hood

Both phones run the same app. The sender uses NFC reader mode to read the other phone as if it were an NFC card, and the receiver uses Host Card Emulation (HCE) to act as that card. The file is sent in small chunks with a simple sequence check, and the receiver confirms each one so a transfer can resume.

## Contributing

Ideas and pull requests are welcome, especially a Bluetooth handoff for faster transfers, bug fixes for specific phones, and a nicer interface.

## Disclaimer

Provided as is, with no warranty. Only send files you're allowed to share.
