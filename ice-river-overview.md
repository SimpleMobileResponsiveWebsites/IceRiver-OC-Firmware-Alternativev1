This document describes a modified firmware for IceRiver ASICs that allows for overclocking and provides various additional features1. Here's a breakdown:

What it is: The firmware is a replacement for the original software on IceRiver ASIC mining devices, giving users more control and information1. It's designed to enhance performance and provide better monitoring capabilities12.

Key Features:

Overclocking: The firmware allows users to adjust the clock speed and voltage of the ASIC, which can lead to increased hashrate1345. 

It is important to note that there are no safety limits enforced by this firmware on either clock or voltage, so users should use it with care6.

Fan Control: It includes improved fan controls that can automatically adjust fan speed to maintain a target temperature6.

Monitoring: The firmware provides detailed graphs of chip metrics, including temperature, hashrate, voltage, and clock speed27. It also tracks uptime and job rates on the pool status89.

Pool Health Monitoring: The firmware includes features to monitor the health of the mining pool connection and will switch back to the primary pool if a secondary is in use and the primary becomes available81011.

Security: The firmware improves security with new authentication and authorization routines and redirects all traffic over HTTPS812. It also includes TLS certificate management1314.

API: There is a new API available for accessing the additional features811.

User Interface (UI): The firmware offers a dark mode, auto-refresh controls, responsive design, and other UI improvements15.

Installation: The firmware is installed like a standard firmware update package16. It is important to note that the firmware should NOT be installed over the xyys firmware on KS0 Ultras or KS5 models. Users should follow the uninstallation instructions before installing this or any other firmware16. If issues occur, try restoring factory settings, restarting the machine, uploading the firmware, and refreshing the web page17.

Fee: There is a 1% fee for the base version of this firmware, with a different fee structure for a commercial/hosting version that has additional features1819. The fee traffic is directed to a specific pool address, and if the system cannot connect to one of the closest Herominers pools, overclocking will be disabled19.

Important Considerations:

IP Addresses: IceRiver ASICs use static IP settings, which may need to be reserved in your router to avoid connection issues20.

DNS Issues: Some ISPs may have issues with the domain name used by the firmware, which can be resolved by updating your DNS server21.

Router Protections: Some router security features may interfere with mining traffic22.

Third-Party Tools: There may be incompatibilities between this firmware and third party management and monitoring tools23.

Power: It is important to use the correct power supply for your model and have a power meter to ensure you stay within your PSU limits. Laptop power supplies should be 19.5V with 5.5mm x 2.5mm connectors17.

Cooling: Proper cooling is essential, especially for KS0 Pro and Ultra models, with hardware modifications for improved cooling recommended. Hash chips generally perform best in the 75-80C range, but this may vary by model2425.

Tuning: The clock offset percentage should equal the hashrate increase percentage on a healthy machine, and a process of gradually increasing clock speed and voltage is recommended52526.

Hashrate Measurement: The document cautions that hashrate measurements on the ASIC UI may not align with those from pools due to different difficulty settings and potential reporting issues. Longer measurement periods are necessary to obtain statistically relevant data2728293031.
●
Reproducing Results: If you are trying to reproduce results from another firmware, you should set the clock offset to match the hashrate increase you previously saw and increase the voltage one step at a time to reach the expected level532.
In summary, this custom firmware is designed to give IceRiver ASIC users more control over their devices, with a focus on overclocking, monitoring, and security128. However, it's also emphasized that users need to be careful and understand the implications of overclocking, as well as the nuances of hashrate measurement62728.
keep_pinSave to note
