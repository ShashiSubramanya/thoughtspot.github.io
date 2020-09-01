To configure a reverse SSH tunnel, navigate to the Administration Portal by clicking on the **Admin** tab from the top navigation bar. Select **Reverse SSH** from the side navigation bar that appears.

![Admin Portal - reverse SSH]({{ site.baseurl }}/images/admin-portal-reverse-ssh.png "Admin Portal - reverse SSH")

Select **Edit** to enable or disable the tunnel.

The **Edit Reverse SSH Tunnel** dialog box appears.

![Edit reverse ssh tunnel]({{ site.baseurl }}/images/admin-portal-reverse-ssh-edit.png "Edit reverse ssh tunnel")

The system asks if you have added `tunnelrelay.thoughtspot.com` to your list of allowed domains.

If you select **no**, you cannot enable or disable the reverse SSH tunnel:

![tunnelrelay.thoughtspot.com not on list of allowed domains]({{ site.baseurl }}/images/admin-portal-reverse-ssh-not-allowed.png "tunnelrelay.thoughtspot.com not on list of allowed domains")

If you have added `tunnelrelay.thoughtspot.com` to your list of allowed domains, by opening port `22`, the system allows you to enable or disable the reverse SSH tunnel.

![Enable the reverse SSH tunnel]({{ site.baseurl }}/images/admin-portal-reverse-ssh-enable.png "Enable the reverse SSH tunnel")

Make the necessary changes and select **OK**.