# openwrt_d-link-TL-WA850RE_V1 21.02.0 RC4
# openwrt_d-link-TL-WA854RE_V1 21.02.0 RC4

for build remove in:
openwrt/package/kernel/mac80211/files/lib/wifi/mac80211.sh

    set wireless.radio${devidx}.disabled=1

this will enable wireless by default and you can connect to 854V1 via wifi.

and

for build edit in: openwrt/target/linux/ath79/image/tiny-tp-link.mk
for 850V1:

    TPLINK_HWID := 0x08500001  
    
or for 854V1  , rest stays:

    TPLINK_HWID := 0x08540001

example 854V1:

    define Device/tplink_tl-wa850re-v1
      $(Device/tplink-4mlzma)
      SOC := ar9341
      DEVICE_MODEL := TL-WA850RE
      DEVICE_VARIANT := v1
      TPLINK_HWID := 0x08540001
       DEVICE_PACKAGES := rssileds
      SUPPORTED_DEVICES += tl-wa850re
    endef
    TARGET_DEVICES += tplink_tl-wa850re-v1
 
and build as it would be an 850V1, even if it is an 854V1.

be care that the maximum filesize (sysupgrade) shoud not bigger than about 3,5 MB. but flash the factory-image.
https://openwrt.org/docs/guide-user/additional-software/saving_space    and use default strip options.


# Note
use precompiled images, such as mine only for testing, build always your own.


