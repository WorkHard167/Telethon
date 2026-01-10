def txt_to_vcf(txt_file, vcf_file):
    with open(txt_file, 'r') as file:
        lines = file.readlines()

    with open(vcf_file, 'w') as vcf:
        for line in lines:
            name, phone = line.strip().split(',')
            vcf.write("BEGIN:VCARD\n")
            vcf.write("VERSION:3.0\n")
            vcf.write(f"N:{name};;;\n")
            vcf.write(f"FN:{name}\n")
            vcf.write(f"TEL;TYPE=CELL:{phone}\n")
            vcf.write("END:VCARD\n")

    print(f"File VCF berhasil dibuat: {vcf_file}")

# Contoh penggunaan:
txt_to_vcf("kontak.txt", "kontak.vcf")
