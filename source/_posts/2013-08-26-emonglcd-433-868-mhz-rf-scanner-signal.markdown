---
layout: post
title: 'emonGLCD 433 / 868 Mhz RF Scanner & Signal Strength Meter '
date: '2013-08-26T07:27:00.003-07:00'
author: Glyn Hudson
categories:
- emonGLCD
- RFM12
modified_time: '2013-08-26T07:34:27.925-07:00'
thumbnail: http://3.bp.blogspot.com/-S0m9P9FKx18/UhtmSquXvUI/AAAAAAAAjn8/d7rcJjPtYM0/s72-c/glcdssm_intf.jpg
blogger_id: tag:blogger.com,1999:blog-2472065242652647619.post-1775753655261807540
blogger_orig_url: http://openenergymonitor.blogspot.com/2013/08/emonglcd-433-868-mhz-rf-scanner-signal.html
---

<a href="http://openenergymonitor.org/emon/user/1824">Martin Roberts</a> has developed a fantastic bit of firmware for the emonGLCD to enable it to be used as an RF scanner and signal strength meter on the 433 / 868 Mhz RF band.<br /><br />&nbsp;This makes the emonGLCD running this firmware a useful tool for debugging RF transmission and checking out signal strength.  To run the firmware a small hardware modification is required to the emonGLCD to access the analogue signal strength output signal from the RFM12B.<br /><br />Martin's sketch has been added to the <a href="https://github.com/openenergymonitor/EmonGLCD/tree/master/GLCD_SSM">emonGLCD github repo</a>.<br /><br />Full details including build-guide and discussion can be found on the original&nbsp;<a href="http://openenergymonitor.org/emon/node/2395">forum thread</a>.<br /><br /><div class="separator" style="clear: both; text-align: center;"><a href="http://3.bp.blogspot.com/-S0m9P9FKx18/UhtmSquXvUI/AAAAAAAAjn8/d7rcJjPtYM0/s1600/glcdssm_intf.jpg" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="300" src="http://3.bp.blogspot.com/-S0m9P9FKx18/UhtmSquXvUI/AAAAAAAAjn8/d7rcJjPtYM0/s400/glcdssm_intf.jpg" width="400" /></a></div><div class="separator" style="clear: both; text-align: center;"><br /></div><div class="separator" style="clear: both; text-align: center;"><br /></div><div class="separator" style="clear: both; text-align: center;"><a href="http://openenergymonitor.org/emon/sites/default/files/GLCD_SSM_interface.jpg" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="579" src="http://openenergymonitor.org/emon/sites/default/files/GLCD_SSM_interface.jpg" width="640" /></a></div><div class="separator" style="clear: both; text-align: center;"><br /></div><div class="separator" style="clear: both; text-align: center;"><a href="http://openenergymonitor.org/emon/sites/default/files/GLCD_SSM_inside.jpg" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" height="302" src="http://openenergymonitor.org/emon/sites/default/files/GLCD_SSM_inside.jpg" width="400" /></a></div><div class="separator" style="clear: both; text-align: center;"><br /></div>