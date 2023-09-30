## 09/29/2023 experimented with adding isFinal flag to onSpeechResults (hash #8b53288f and d5024a37).
It turns out the isFinal flag is never set to true even when one is done speaking.  This is confirmed from Apple's support (Luis's email).  The only time isFinal is true is when Voice.stop() is called.
