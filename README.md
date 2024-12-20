# Setting Up VPN Using AmneziaWG Protocol on Keenetic Router

This guide assumes you already have the configuration file for AmneziaWG that you wish to run on your Keenetic router.

KeeneticOS supports the AmneziaWG protocol starting from version 4.2. Specifically, KeeneticOS 4.2.1 allows importing the AmneziaWG configuration as a standard WireGuard configuration. You can further adjust the asc parameters (Jc, Jmin, Jmax, S1, S2, H1, H2, H3, H4) through the KeeneticOS command line interface (CLI).

## Update your router to KeeneticOS 4.2 or later.
Make sure your router is running an updated version of the operating system.

## Check that the WireGuard component is installed:
Go to **System Settings** → **Component options** → **WireGuard VPN** → Ensure it’s Installed.

## Import your AmneziaWG configuration file (\*.conf):
Navigate to **Other Connections** → **WireGuard** → **Upload from a file** → Select your AmneziaWG config file (*.conf).

## Enable internet access through the newly created connection:
In the WireGuard list, select your newly imported connection and check **Use for accessing the internet**. Save the changes.

## Note the connection name:
This will either be the name of your *.conf file or the name you assigned during import.

## Open the Command Line Interface (CLI) in KeeneticOS:
Click the gear icon in the top-right corner → **Command line**.

## Enter the following command in CLI:
Type 'show interface' and click **Send request**.

## Find the interface name:
Look for your connection’s name under the 'description' parameter. Adjacent to it, you’ll find the 'interface-name' parameter. This is what you’ll need.

## Locate the asc parameters in your AmneziaWG config file:
Open your AmneziaWG configuration file and locate the values for `Jc`, `Jmin`, `Jmax`, `S1`, `S2`, `H1`, `H2`, `H3`, and `H4`.

## Form the CLI command:

Now that you have the interface name and the asc values from the AmneziaWG config file (*.conf), replace the placeholder values with your own and remove the curly braces:

`interface {interface-name} wireguard asc {jc} {jmin} {jmax} {s1} {s2} {h1} {h2} {h3} {h4}`

## Example:

If your interface name is Wireguard1 and your asc parameters are `3 40 80 35 90 129283290 8726729867 194782156 543347908`, the final string would look like:

`interface Wireguard1 wireguard asc 3 40 80 35 90 129283290 8726729867 194782156 543347908`

## Submit the command:

Paste the string into the CLI and click **Send request**.

## Your VPN connection via the AmneziaWG protocol is now active.

The last step is to configure the connection policies for your devices under the Connection Priorities section.

By following these steps, you’ll have successfully configured your Keenetic router to use the AmneziaWG protocol for VPN connections.

## Official Amnezia guide for KeeneticOS

Here is the official Amnezia guide for KeeneticOS in Russian with images: https://docs.amnezia.org/documentation/instructions/keenetic-os-awg/
