# patch-openstack-swift
LightSync patch on OpenStack Swift

<H1> How to Deploy Patch: </H1>
<H3> Requirement: </H3>
This patch requires OpenStack Swift Icehouse installed and should be applied on all storage nodes.
<H3> Deployment: </H3>
<ol>
  <li><h5>Locate the <i>swift</i> Python package</h5>
      <p>This can be done by running Python, then executing:<br>
        <code>>>> import swift</code><br>
        <code>>>> swift.__path__</code><br>
      </p>
      <p>On our cluster the output is <i><b>['/usr/lib/python2.7/dist-packages/swift']</b></i>, <br>
      Which means the swift package location is <i>/usr/lib/python2.7/dist-packages/swift</i></p>
  </li>
  <li><H5>append the <i>obj</i> directory to swift package location</H5>
    This give <i>swift-package-location/obj</i>. in our cluster will be <i><b>/usr/lib/python2.7/dist-packages/swift/obj</b></i>
  </li>
  <li><H5>Patching</H5>
    Copy patch files(<i>replicator.py</i> and <i>diskfile.py</i>) to the extended path(<i>/usr/lib/python2.7/dist-packages/swift/obj</i>), 
    replacing the existing ones.
  </li>
  <li><H5>Restart Openstack Swift object-server and object-replicator</H5>
      swift-init restart object-server object-replicator
  </li>
</ol>


