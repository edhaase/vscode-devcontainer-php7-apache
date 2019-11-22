Debugging
===

This application can be debugged via xdebug, and supports vscode breakcodes.

The following instructions all expect vscode to be attached to `.devcontainer` at time of usage.

## Setup

Under the debug tab of vscode, select add configuration and add the `Listen for XDebug` configuration.

## Starting a debug session

In order to debug a php application, vscode must be listening for an xdebug session. Under the debug tab, launch the `Listen for XDebug` config. You should see a debugging bar appear along
the top center of your screen. You're now ready to debug!
