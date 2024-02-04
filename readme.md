# Generate arbitrary waveform on Siglent SDG1032X

The Siglent SDG1032X has the ability to play arbitrary (user-programmed) waveforms. These waveforms can be produced using the Siglent EasyWave software. This (I think) only runs on Windows. Besides (also I think) does not have much control over the produced waveform to get any scientific value from it. There are also other methods to produce arbitrary waveforms on the SDG1032X.

- by importing  from an USB stick
- by using SCPI commands from a computer
- by using PyVISA from a computer

I wrote Python scripts to use them all. It appears that using SCPI (although it would be the easiest way to get waveforms on the sdg) an ugly bug in the SDG1032X firmware appears. This bug treats any \x0a value in the bytestream sent to it as a termination character, also if this \x0a is part of the values in the waveform. This results in corrupt data in the SDG1032X and lock-ups. This bug also appears in some form using the PyVISA package. Using transfer by USB-stick does not cause the bug to appear.

See [here](https://www.eevblog.com/forum/testgear/siglent-sdg1032x-bug-in-user-defined-waveforms/msg4677745/#msg4677745) for more on this bug.

Before running the scripts:

```
pip install matplotlib
pip install numpy
pip install pyvisa
pip install pyvisa-py
```

