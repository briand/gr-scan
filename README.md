gr-scan
=======

Frequency scanner for gnuradio. Updated/forked from http://www.techmeology.co.uk/gr-scan/

Builds on OS X 10.7.5 with some minor warnings, and works fine for the most part. You'll need gnuradio, gr-osmosdr, boost and argp installed to build (homebrew calls the latter "argp-standalone"). gr-scan uses the osmosdr source block so it will run on rtlsdr devices as well as others such as HackRF and BladeRF. Converting back to build on Linux should be simply a matter of changing clang++ to g++ (4.7-ish or later) and probably removing the C++0x11 switch.

(below description taken from the original author's page)

Introduction
============

gr-scan is a program written in C++, and built upon GNU Radio, rtl-sdr, and the OsmoSDR Source Block. It is intended to scan a range of frequencies and print a list of discovered signals. It should work with any device that works with that block, including Realtek RTL2832U devices. I developed this software using a Compro U620F, which uses an E4000 tuner. That product doesn't seem to be available on the US site, but the Newsky DVB-T Receiver (RTL2832U/E4000 Device) has good reviews. The current version of gr-scan is: 2012082301.

Building and Running
====================

These instructions are intended for a GNU/Linux installation, however it should be possible to adapt gr-scan for use on other platforms.

Ensure GNU Radio, rtl-sdr, and the OsmoSDR Source Block are installed [ed: see the updated requirements above]. You will also require a recent version of GCC: to support the new for loops introduced by C++11. You might be able to compile it with GCC 4.6, but I recommend 4.7 or greater.
Download and extract the gr-scan Source Archive.
Change to the source directory, edit the Makefile if necessary, and run make.
For a simple scan between 99 and 101 MHz (actually a little extra at each side), run
```
./gr-scan -x 99 -y 101
```
To search for intermittent signals, such as amateur radio try something like
```
./gr-scan -x 144 -y 146 -p 600
```
This will cause gr-scan to keep listening on each frequency for 600 seconds (10 minutes). For a complete list of options, see
```
./gr-scan --help
```
