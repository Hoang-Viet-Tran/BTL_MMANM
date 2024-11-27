# Single-sign-on (SSO)
## Nguyên lý hoạt động
Một miền trung tâm (central domain) thường đóng vai trò là Identity Provider (IdP), qua đó xác thực được thực hiện và phiên được chia sẻ với các miền khác
## Một số giải pháp SSO thông dụng
1. SAML
Xác nhận SAML (SAML assertions): được tạo ra và sử dụng để xác minh danh tính người dùng và cung cấp các dịch vụ mà người dùng có thể truy cập
- SAMLAuthnRequest: là yêu cầu xác thực người dùng gửi từ phía Service Provider (SP) tới IdP, thường bao gồm các thành phần sau:

 <samlp:AuthnRequest
     xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol"
     xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion"
     ID="ONELOGIN_809707f0030a5d00620c9d9df97f627afe9dcc24"
     IssueInstant="2014-07-16T23:52:45Z"
     Destination="http://idp.example.com/SSOService.php"
     ProtocolBinding="urn:oasis:names:tc:SAML:2.0:bindings:HTTP - POST"
     AssertionConsumerServiceURL="http://sp.example.com/demo1/index.php?acs">
     <saml:Issuer>
         http://sp.example.com/demo1/metadata.php
     </saml:Issuer>
     <samlp:RequestedAuthnContext Comparison="exact">
         <saml:AuthnContextClassRef>
             urn:oasis:names:tc:SAML:2.0
     :ac:classes:PasswordProtectedTransport
         </saml:AuthnContextClassRef>
     </samlp:RequestedAuthnContext>
 </samlp:AuthnRequest>

- SAMLResponse: là phản hồi yêu cầu xác thực từ IdP gửi đến SP, bao gồm:

<samlp:Response
    xmlns:samlp="urn:oasis:names:tc:SAML:2.0:protocol"
    xmlns:saml="urn:oasis:names:tc:SAML:2.0:assertion"
    ID="_8e8dc5f69a98cc4c1ff3427e5ce34606fd672f91e6"
    IssueInstant="2014-07-17T01:01:48Z"
    Destination="http://sp.example.com/demo1/index.php?acs"
    InResponseTo="
  ONELOGIN_4fee3b046395c4e751011e97f8900b5273d56685">
    <saml:Issuer>
        http://idp.example.com/metadata.php
    </saml:Issuer>
    <samlp:Status>
        <samlp:StatusCode
            Value="urn:oasis:names:tc:SAML:2.0:status:Success"/>
    </samlp:Status>
    <saml:Assertion
        ID="_d71a3a8e9fcc45c9e9d248ef7049393fc8f04e5f75"
        IssueInstant="2014-07-17T01:01:48Z">
        <saml:Issuer>
            http://idp.example.com/metadata.php
        </saml:Issuer>
        <saml:Subject>
            <saml:NameID
                SPNameQualifier="http://sp.example.com/demo1/metadata.php"
            </saml:NameID>
        </saml:Subject>
        <saml:Conditions
            NotBefore="2014-07-17T01:01:18Z"
            NotOnOrAfter="2024-01-18T06:21:48Z">
        </saml:Conditions>
        <saml:AttributeStatement>
            <saml:Attribute Name="uid"
                NameFormat="urn:oasis:names:tc:SAML:2.0:attrname - format:basic">
                <saml:AttributeValue xsi:type="xs:string">
                    test
                </saml:AttributeValue>
            </saml:Attribute>
        </saml:AttributeStatement>
    </saml:Assertion>
</samlp:Response>

-
