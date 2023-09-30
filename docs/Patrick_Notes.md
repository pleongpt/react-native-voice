## 09/29/2023 experimented with adding isFinal flag to onSpeechResults (hash #8b53288f and d5024a37).
It turns out the isFinal flag is never set to true even when one is done speaking.  This is confirmed from Apple's support (Luis's email).  The only time isFinal is true is when Voice.stop() is called.

If shouldReportPartialResults is set to false, then isFinal flag is only set to true after 60 seconds of silence.

Therefore, the best way to fix this is to implement a timer that watch for silence of certain duration.  If there is any new STT text coming in, then this timer is invalidated and restart again.  If the timer is finally called, then the STT result is sent to the caller.
