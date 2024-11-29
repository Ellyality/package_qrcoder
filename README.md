# package_qrcoder

A package that simply generate the qrcode\
This package use [qrcoder](https://github.com/codebude/QRCoder) dependency\
For any problem that need to be solve beyond qrcode texture 2d generation, you can go here.

## How To Use It ?

We need below elements in order to generate a QR code texture2D target

```csharp
public class QRHandler : MonoBehaviour
{
  RawImage ima;
  QRCodeGenerator generator;
  QRCodeData qrdata;
  UnityQRCode qr;
  Texture qrtex;
}
```

Let's init the generator first, this can be reuse afterward

```csharp
private void Start()
{
    generator = new QRCodeGenerator();
}
```

Create a set data function\
ProtestTopTest is RawImage instance

```csharp
public void SetData(string d)
{
    qrdata = generator.CreateQrCode(d, QRCodeGenerator.ECCLevel.Q);
    qr = new UnityQRCode(qrdata);
    qrtex = qr.GetGraphic(20);
    ima.texture = qrtex;
}
```
