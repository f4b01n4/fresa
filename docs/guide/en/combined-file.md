# One file with tool changes

In **Result → Output**, turn on **Single file with tool changes (M0)**. Fresa
writes `combined.nc` with every operation in order. At each tool change:

1. The spindle stops and the machine pauses with a message
   (*TOOL CHANGE 1/2: …*).
2. Change the tool, set it 1–10 mm above the copper by sliding it in the
   collet, clip the probe to it, and **Resume** (Machine tab, or the WebUI).
3. The new tool touches the copper twice (fast, then slow) and Z is zeroed.
4. A second pause asks you to remove the clip. **Resume** again: the spindle
   starts and cutting continues.

The probe point defaults to where you first zeroed Z. Fresa warns in red when
the point is on a copper island that the isolation cuts off (the clip would not
see the contact), on a groove, or on a hole. Before trusting it on copper, run
the file once in check mode (`$C`, then `$SD/Run=/combined.nc`, then `$C`).
