# Hotspot2.0 / WPA2-3-Enterprise Wi-Fi QR code specification

This very simple project attempts to introduce a simple way of deploying both Hotspot2.0 and WPA2/3-Enterprise Wi-Fi profiles on iOS devices. 

A web portal is required to generate the QR code according to the schema definition below. The JSON object must be then BASE64 encoded before generating the QR image. 

The EAP method will, of course, be username & password based. Depending on the application using the QR code, it can be provisioned as EAP-PEAP or EAP-TTLS with inner MSCHAPv2 for example. 

## JSON Schema Example

```
{
    "ssid":"",
    "domain":"example.com",
    "anonymous":"example.com",
    "rcoi":["012345"],
    "username":"sample_username",
    "password":"sample_password",
    "naiRealmNames":["domain.tld", "example.com"],
    "servernames":["*.eap-domain.tld"]
}
```

## JSON Field Definitions

| Field Name | Value |
| ----------- | ----------- |
| ssid | **Optional**. If provided, the QR code indicates a non-802.11u WPA-Enterprise network. |
| domain | **Must be empty** for WPA-Enterprise, **Required** for 802.11u |
| anonymous | **Optional**. If provided, then the profile will provision an anonymous external identify under the specified domain. |
| rcoi | **Required** only for 802.11u | 
| username | **Required** |
| password | **Required** in plain text | 
| naiRealNames | Array. **Required** only for 802.11u | 
| servernames | Array. **Required** for EAP server name validation in all scenarios| 