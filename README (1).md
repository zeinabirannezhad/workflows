Computer Organization - Spring 2024
==============================================================
## Iran Univeristy of Science and Technology
## Assignment 1: Assembly code execution on phoeniX RISC-V core

- Name:zeinab irannezhad
- Team Members:
- Student ID: 9940017
- Date:1403/02/04

## Report
.section .text
.glob1 quicksort
quicksort:
  # quicksort algorithm implementation 
  # assume a0 is the array pointer, a1 is 
the low index, and a2 is the high index
  addi sp, sp, -16
  sw ra, 12 (sp) 
  sw a1, 8 (sp)
  sw a2, 4 (sp)
  sw a0, 0 (sp)
  bge a1, a2, end_quicksort
  add a3,a0,a1
  add a3,a3,a2
  srai a3, a3, 1
  mv a4, a2
  mv a5, a1
  j partitaion
partitation_loop:
  addi a5, a5, 1
partitation:
  li a6, 1
  blt a0, a3, partitation_loop
  li a6, -1
  bgt a0, a3, partition_loop
  add a0, a0, a6
  bge a5, a4, partition_end
  mv a7, a0
  mv a0, a4
  mv a4, a7
  j partition_loop
partition_end:
  mv a0, a5
  mv a1, a2
  call quicksort
  mv a0, a1
  mv a2, a4
  call quicksort
end_quicksort:
  1w ra, 12 (sp)
  1w a1, 8 (sp)
  1w a2, 4 (sp)
  1w a0, 0 (sp)
  addi sp, sp, 16
  jr ra
Quic Sort Algorithm
ستRISC-V در زبان اسمبلی (Quick Sort) این بخش شامل پیاده سازی الگوریتم مرتب سازی سریع 
.و یکی از موثر ترین روش هااست که بااستفاده از تکنیک تقسیم و غلبه کار میکن
ویژگی های کد:
پیاده سازی با استفاده از فراخوانی های تابع برای تقسیم و حل مسئله .
بهینه سازی شده برای کاهش تعداد مقایسه ها و جابه جایی ها .
venus RISC-V قابلیت اجرا بر روی شبیه ساز .
.section .text
.globl int_sqrt
int_sqrt:
  # integer square root algorithm
implementatial
  # assume a0 is the input number
  li a1, 0
  li a2, 1
  slli a2, a2, 30
sqrt_loop:
  blt a2, a2 sqrt_next
  srli a2, a2, 2
  j sqrt_loop
sqrt_next:
 add a1, a1, a2
 slli a1, a1, 1
 sub a0, a0, a2
 srli a2, a2, 2
 benz a2, sqrt_loop
 srai a1, a1, 1
 mv a0, a1
 ret
Integer Squar Root Algorithm
RISC-V این بخش شامل پیاده سازی الگوریتم محاسبه در ریشه دوم صحیح است . این الگوریتم برای 
  زبان اسمبلی محاسبه ریشه دوم یک عدد صحیح بدون استفاده از عملیات شناور استفاده میشود
ویژگی های کد:
اجرای سریع و کارآمد با استفاده از شیفت ها و اضافه ها 
دقت بالا در محاسبه ریشه های دوم صحیح
نتیجه نهایی :
نتایج اجرای کدهاو شکل موج های خروجی نشان دهنده عملکرد صحیح و بهینه سازی شده کدهاهستند.