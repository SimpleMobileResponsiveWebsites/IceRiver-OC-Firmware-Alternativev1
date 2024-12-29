The document describes the API (Application Programming Interface) for a modified IceRiver ASIC firmware, providing a way to interact with the miner's functions and data programmatically. Here's a summary of the API, drawing from the provided sources:
●
General API Information:
○
Requests are made over HTTPS on port 44312.
○
Requests use HTTP GET or HTTP POST (when parameters are needed)1.
○
Authentication is done via API token using a header of the form Authorization: Bearer <token>13.
○
Parameters are sent in a serialized URL-encoded format1.
○
A basic response includes error and message properties, where success generally looks like {"error": 0, "message": ""}1.
○
Full documentation is available in JSON format2.
●
Key API Endpoints:
○
/api/overview:
■
Description: Gets a combined set of data points, including hashrate, pool info, and hashboard status4.
■
Permissions: Requires view_miner permission4.
■
Response Properties: Includes details such as ASIC model, firmware versions, network information, hashrate data, pool configurations, and hashboard information4567....
○
/api/timeseries:
■
Description: Retrieves a series of data points for graphing17.
■
Permissions: Requires view_miner permission17.
■
Request Properties: Requires a series parameter, which can be boardtemp, chipclock, chiptemp, chipvoltage, fanpwm, fanrpm, or hashrate1718.
■
Response Properties: Returns a multi-dimensional list of series data per minute (5 minutes for hashrate), grouped by board when appropriate1819.
○
/api/machine:
■
Description: Gets the machine state, such as the ASIC model and mode (sleep or normal)1920.
■
Permissions: Requires view_miner permission19.
■
Response Properties: Includes the device model name and the machine's current mode (sleep/normal)20.
○
/api/machine/reboot: Reboots the machine20. Requires edit_miner permission20.
○
/api/machine/shutdown: Powers off the machine20. Requires edit_miner permission20.
○
/api/machine/sleep: Puts the machine in sleep mode20. Requires edit_miner permission20.
○
/api/machine/wake: Wakes the machine from sleep mode2021. Requires edit_miner permission21.
○
/api/machine/reset: Resets the machine to factory settings21. Requires edit_all permission21.
○
/api/machine/ping: Sends a healthcheck request21.
○
/api/machine/locate: Toggles the locator LED on the machine21. Requires edit_all permission21.
○
/api/user/create: Creates a user account21. Requires edit_all permission21. The request must include the username, password, and assigned roles2122.
○
/api/user/list: Lists user accounts22. Requires view_all permission22. Response includes a list of user objects containing id, username, password (null), and roles222324.
○
/api/user/update: Updates a user account24. Requires edit_all or edit_owned permissions24. Allows updates to id, username, password, and roles2425.
○
/api/user/delete: Deletes a user account25. Requires edit_all permission25. The request must include the record id2526.
○
/api/user/roles: Lists valid roles that can be assigned to a user26. Requires view_all permission26. Returns a list of assignable roles like administrator, guest, limited_user, and user2627.
○
/api/token/create: Creates an API token27. Requires edit_owned permission27. The request must include the permissions assigned to the token and the expiry date2728.
○
/api/token/list: Lists API tokens28. Requires view_owned permission28. Response includes a list of token objects containing the token id, token string, the user to whom it belongs, the abilities/permissions granted, and the expiry date2829.
○
/api/token/update: Updates an API token30. Requires edit_owned permission30. Allows updates to the token id, abilities and expiry date3031.
○
/api/token/delete: Deletes an API token31. Requires edit_owned permission31. The request must include the record id3132.
○
/api/token/abilities: Lists valid permissions that can be assigned to a token32. Requires view_owned permission32. The response contains a list of assignable permissions such as edit_miner, view_all, edit_owned, etc32.
○
/api/pool/create: Creates a pool/stratum proxy config3233. Requires edit_pools permission32. The request must include the pool address, wallet, and optional password323334.
○
/api/pool/list: Lists pool/stratum proxy configs34. Requires view_pools permission34. The response contains a list of pool objects including the pool id, address, wallet, and password3435.
○
/api/pool/update: Updates a pool/stratum proxy config35. Requires edit_pools permission35. Allows updates to the pool id, address, wallet, and password353637.
○
/api/pool/delete: Deletes a pool/stratum proxy config36. Requires edit_pools permission36. The request must include the record id37.
○
/api/clock: Gets the clock config37. Requires view_miner permission37. The response includes the base clock frequency and offset3738.
○
/api/clock/update: Sets the clock offset38. Requires edit_miner permission38. The request must include the offset value3839.
○
/api/voltage: Gets the voltage config39. Requires view_miner permission39. The response includes the base voltage level and offset3940.
○
/api/voltage/update: Sets the voltage offset40. Requires edit_miner permission40. The request must include the offset value40.
○
/api/fan: Gets the fan config4041. Requires view_miner permission4041. The response includes the min PWM, mode (auto, fixed or temp), ratio for fixed mode, and target temperature for temp mode41.
○
/api/fan/update: Sets the fan config4142. Requires edit_miner permission4142. Allows updates to the min PWM, mode (auto, fixed, temp), PWM for fixed mode and target temp for temp mode4243.
○
/api/network: Gets the network config43. Requires view_miner permission43. The response includes the network interface controller name, MAC address, IP address, netmask, hostname, DHCP setting, gateway, and DNS server434445.
○
/api/network/update: Sets the network config4546. Requires edit_all permission4546. Allows updates to the IP address, netmask, hostname, DHCP setting, gateway and DNS server4647.
○
/api/network/updateca: Updates the CA certificate or key file47. Requires edit_all permission47. The request must include the file type (cert or key) and the file itself4748.
○
/api/network/regencert: Regenerates the TLS certificate48. Requires edit_all permission48.
○
/api/split/create: Creates a hashrate split4849. Requires edit_all permission48. The request must include the pool address, wallet, hashrate percentage, and optional password484950.
○
/api/split/list: Lists hashrate splits50. Requires view_all permission50. The response contains a list of hashrate split objects including the split id, pool address, wallet, hashrate percentage, and password5051.
○
/api/split/update: Updates a hashrate split5152. Requires edit_all permission5152. Allows updates to the split id, pool address, wallet, hashrate percentage, and password5253.
○
/api/split/delete: Deletes a hashrate split53. Requires edit_all permission53. The request must include the record id5354.
○
/api/firmware/update: Updates the firmware54. Requires edit_all permission54. The request must include the firmware file5455.
○
/api/brand/update: Updates the branding file55. Requires edit_all permission55. The request must include the branding image (112x60 PNG) file55.
●
Permissions:
○
The API uses a granular permission system to control access to different functionalities3.
○
Permissions include: view_miner, edit_miner, view_all, edit_all, edit_owned, and view_owned and edit_pools, view_pools4212224....
○
API tokens can be created with specific permissions, allowing fine-grained access control3.
In summary, the API provides a comprehensive way to manage and monitor IceRiver ASICs, allowing users to retrieve data, modify settings, and perform actions remotely and programmatically, with a strong focus on security and control.

