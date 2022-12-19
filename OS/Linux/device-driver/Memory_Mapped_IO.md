# Memorry mapped IO at Beaglebone black
1. Check reference manual
 https://www.ti.com/lit/ug/spruh73q/spruh73q.pdf?ts=1666670382560&ref_url=https%253A%252F%252Fwww.ti.com%252Fproduct%252FAM3358
2. Mapping address
  ioremap(addr, len)
3. Read/Write value
  ioread32()  
  iowrite32()

  or

  readl()
  writel()

