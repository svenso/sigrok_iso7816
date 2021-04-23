# Sigrok ISO7816 (Smartcard) decoder

This sigrok decoder helps parsing Smartcard data recorded by a digital signal processor.

For example it can be used to sniff SIM-Card data:

![SIM-Sniff](https://raw.githubusercontent.com/svenso/sigrok_iso7816/main/resources/sim_sniff.jpg)

The examples directory holds a SIM-sniff sample and the corresponding pcap.

## T=0
![T=0 sample](https://raw.githubusercontent.com/svenso/sigrok_iso7816/main/resources/paymentcard_t0.PNG)

![T=0 wireshark](https://raw.githubusercontent.com/svenso/sigrok_iso7816/main/resources/paymentcard_t0_wireshark.PNG)
## T=1
![T=1 sample](https://raw.githubusercontent.com/svenso/sigrok_iso7816/main/resources/mastercard_t1.PNG)

## FAQs
- How to export to PCAP?
    > "sigrok-cli.exe" --loglevel 1 -P iso7816:clk=0:data=2:clock_option=detect --input-file "PC_7_123456_46824768_wrong_pin.vcd" --input-format vcd -B iso7816=pcap > PC_7_123456_46824768_wrong_pin.pcap
- What is clock_option?
    - native
        > use the native clock and specifications from ISO+IEC 7816-3-2006 (or sort of them :P). Good if you recorded the sample with enough high samplerate (usually about 10MHZ)
    - detect
        > try detecting the specifications (requires the first communication be an ATR). Most stable, even works if clock does not have the correct resolution.
    - sample_as_clock
        > uses sample as a clock (might be working in few circumstances). Experiment
- Is error handling on phy implemented?
    > no. if you got sample recordings with phys-errors, feel free to provide them.
- Supported Protocols
    > T=0 and T=1 (a bit)



