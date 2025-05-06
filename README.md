# redes2_ipv6

<?xml version="1.0"?>
<core>
  <session>

    <node id="1" name="router">
      <position x="300.0" y="200.0"/>
      <interface id="0" name="eth0">
        <ip address="2001:db8:1::1/64"/>
      </interface>
      <interface id="1" name="eth1">
        <ip address="2001:db8:2::1/64"/>
      </interface>
      <interface id="2" name="eth2">
        <ip address="2001:db8:3::1/64"/>
      </interface>
      <interface id="3" name="eth3">
        <ip address="2001:db8:4::1/64"/>
      </interface>
      <model>router</model>
      <services>
        <service>DefaultRoute</service>
        <service>IPv6Forwarding</service>
      </services>
      <commands>
        <command>sysctl -w net.ipv6.conf.all.forwarding=1</command>
      </commands>
    </node>

    <node id="2" name="host1">
      <position x="100.0" y="100.0"/>
      <interface id="0" name="eth0">
        <ip address="2001:db8:1::2/64"/>
      </interface>
      <commands>
        <command>ip -6 route add 2001:db8:2::/64 via 2001:db8:1::1</command>
        <command>ip -6 route add 2001:db8:3::/64 via 2001:db8:1::1</command>
        <command>ip -6 route add 2001:db8:4::/64 via 2001:db8:1::1</command>
      </commands>
    </node>

    <node id="3" name="host2">
      <position x="100.0" y="200.0"/>
      <interface id="0" name="eth0">
        <ip address="2001:db8:2::2/64"/>
      </interface>
      <commands>
        <command>ip -6 route add 2001:db8:1::/64 via 2001:db8:2::1</command>
        <command>ip -6 route add 2001:db8:3::/64 via 2001:db8:2::1</command>
        <command>ip -6 route add 2001:db8:4::/64 via 2001:db8:2::1</command>
      </commands>
    </node>

    <node id="4" name="host3">
      <position x="100.0" y="300.0"/>
      <interface id="0" name="eth0">
        <ip address="2001:db8:3::2/64"/>
      </interface>
      <commands>
        <command>ip -6 route add 2001:db8:1::/64 via 2001:db8:3::1</command>
        <command>ip -6 route add 2001:db8:2::/64 via 2001:db8:3::1</command>
        <command>ip -6 route add 2001:db8:4::/64 via 2001:db8:3::1</command>
      </commands>
    </node>

    <node id="5" name="host4">
      <position x="100.0" y="400.0"/>
      <interface id="0" name="eth0">
        <ip address="2001:db8:4::2/64"/>
      </interface>
      <commands>
        <command>ip -6 route add 2001:db8:1::/64 via 2001:db8:4::1</command>
        <command>ip -6 route add 2001:db8:2::/64 via 2001:db8:4::1</command>
        <command>ip -6 route add 2001:db8:3::/64 via 2001:db8:4::1</command>
      </commands>
    </node>

    <!-- Links -->
    <link>
      <node id="1" interface="0"/>
      <node id="2" interface="0"/>
    </link>
    <link>
      <node id="1" interface="1"/>
      <node id="3" interface="0"/>
    </link>
    <link>
      <node id="1" interface="2"/>
      <node id="4" interface="0"/>
    </link>
    <link>
      <node id="1" interface="3"/>
      <node id="5" interface="0"/>
    </link>
  </session>
</core>
