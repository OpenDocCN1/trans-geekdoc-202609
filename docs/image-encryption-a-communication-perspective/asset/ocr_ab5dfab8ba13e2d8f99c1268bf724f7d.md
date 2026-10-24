# OFDM LIMITATIONS

# 8.1 Introduction

OFDM has been adopted in the European digital audio and video broadcasting radio system and is being investigated for broadband indoor wireless communications. Standards such as High-Performance Radio Local-Area Network (HIPERLAN2), Institute of Electrical and Electronics Engineers (IEEE) 802.11a, and IEEE 802.11g have emerged to support services based on the Internet Protocol (IP). Such systems are based on OFDM and are designed to operate in the 5-GHz band [147].

Unfortunately, OFDM communication systems have two primary problems: the high sensitivity to carrier frequency offsets (CFOs) and the high peak-to-average power ratio (PAPR). The sensitivity to CFOs breaks the subcarriers’ orthogonality, and the high PAPR requires system components with a wide linear range to accommodate for the signal variations. Otherwise, nonlinear distortion, which results in a loss of subcarrier orthogonality and hence a degradation in the system performance, occurs [148–152].

Researchers have proposed various methods to combat the intercarrier interference (ICI in OFDM systems. The existing approaches that have been developed to reduce ICI can be categorized into frequency domain equalization, time domain windowing, and self-cancellation (SC) schemes. In addition, statistical approaches have been explored to estimate and cancel ICI. In this chapter, the effects of CFO and PAPR problems are studied with solutions to these problems and to reduce their effects on the transmitted encrypted images.