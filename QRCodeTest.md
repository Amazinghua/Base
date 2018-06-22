##c#生成二维码 ##

                            case "testQR":
                            string strCode = "王天华";
                            QRCodeGenerator qrGenerator = new QRCoder.QRCodeGenerator();
                            QRCodeData qrCodeData = qrGenerator.CreateQrCode(strCode, QRCodeGenerator.ECCLevel.Q);
                            QRCode qrcode = new QRCode(qrCodeData);

                            // qrcode.GetGraphic 方法可参考最下发“补充说明”
                            Bitmap qrCodeImage = qrcode.GetGraphic(5, Color.Black, Color.White, null, 15, 6, false);
                            MemoryStream ms = new MemoryStream();
                            qrCodeImage.Save(ms, ImageFormat.Jpeg);
                            qrCodeImage.Save("C:\\Users\\Administrator\\Desktop\\test.jpg");
                            break;
