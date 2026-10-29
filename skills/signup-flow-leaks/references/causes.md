# Common causes at a drop, and what proves each

- **Dead tap:** taps on the button with no navigation or change. Proof: 3 tries in fresh pages, no response.
- **Error on click:** a first-party JavaScript error right after the tap. Proof: the stack and the file.
- **Slow response:** the tap works but nothing shows for several seconds. Proof: timing from the recording.
- **Form rejects input:** a field error the visitor can't see on a phone. Proof: the field and the message.
- **OAuth or email loop:** the visitor leaves for Google or email and never returns. Proof: the start and return
  counts for that step.
