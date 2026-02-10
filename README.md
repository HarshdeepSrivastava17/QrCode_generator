# Qr_code_generator
I have make a project Using python to generate a Qr-code. 
import qrcode
from PIL import Image

class QREncoder:
    def __init__(self, data, version=None, box_size=10, border=4):
        self.data = data
        self.version = version
        self.box_size = box_size
        self.border = border

    def encode(self):
        qr = qrcode.QRCode(
            version=self.version,
            box_size=self.box_size,
            border=self.border,
        )
        qr.add_data(self.data)
        qr.make(fit=True)
        img = qr.make_image(fill_color="black", back_color="white")
        return img

# Example usage
if __name__ == "__main__":
    data = "https://youtu.be/MoLaqosHlyY?si=JeM-3BeUKQ2r9ISB"
    encoder = QREncoder(data)
    qr_code = encoder.encode()
    qr_code.save("my_qr_code.png")
    print("QR Code generated successfully!")

    # Display the QR code
    qr_code.show()
