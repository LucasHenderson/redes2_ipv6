# redes2_ipv6

<?xml version="1.0"?>
<core>
  <session>

    <!-- Roteador -->
    <node id="1" name="router">
      <position x="400.0" y="300.0"/>
      <model>router</model>
      <services>
        <service>DefaultRoute</service>
        <service>IPv6Forwarding</service>
      </services>
    </node>

    <!-- Hosts -->
    <node id="2" name="host1">
      <position x="100.0" y="100.0"/>
    </node>
    <node id="3" name="host2">
      <position x="100.0" y="200.0"/>
    </node>
    <node id="4" name="host3">
      <position x="100.0" y="300.0"/>
    </node>
    <node id="5" name="host4">
      <position x="100.0" y="400.0"/>
    </node>

    <!-- Links com IPs configurados -->
    <link>
      <node id="1">
        <interface id="0" name="eth0">
          <ip address="2001:db8:1::1/64"/>
        </interface>
      </node>
      <node id="2">
        <interface id="0" name="eth0">
          <ip address="2001:db8:1::2/64"/>
        </interface>
      </node>
    </link>

    <link>
      <node id="1">
        <interface id="1" name="eth1">
          <ip address="2001:db8:2::1/64"/>
        </interface>
      </node>
      <node id="3">
        <interface id="0" name="eth0">
          <ip address="2001:db8:2::2/64"/>
        </interface>
      </node>
    </link>

    <link>
      <node id="1">
        <interface id="2" name="eth2">
          <ip address="2001:db8:3::1/64"/>
        </interface>
      </node>
      <node id="4">
        <interface id="0" name="eth0">
          <ip address="2001:db8:3::2/64"/>
        </interface>
      </node>
    </link>

    <link>
      <node id="1">
        <interface id="3" name="eth3">
          <ip address="2001:db8:4::1/64"/>
        </interface>
      </node>
      <node id="5">
        <interface id="0" name="eth0">
          <ip address="2001:db8:4::2/64"/>
        </interface>
      </node>
    </link>

  </session>
</core>


