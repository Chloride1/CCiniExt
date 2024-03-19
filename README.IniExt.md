## Chloride.RA2.IniExt
��������ڴ����ע�� Ares INI��ͬʱ��`pyalert2yr`��Ŀ��`ini`ģ�����չ��ԭ��ֻ����ֵ�����

### Ϊ���� Ares INI��

Ares �ǡ���ɫ����2������ĸ��𡷵���չƽ̨������ ini ����������һЩԼ����
- ����[Ƕ��](https://ares-developers.github.io/Ares-docs/new/misc/include.html) `[#include]`  
	���Բ������� ini����ͨ��`[#include]`���ϵ�һ�𡣵��� C ��ͬ���ǣ��� ini ���ڸ��ļ�����֮���ٶ�ȡ����ȡ���̵ݹ���С�

- ����̳� `[Child]:[Parent]`  
	�� Ares ��ʵ�����������ڴ濽������˸�С�ڱ���������ӽ�֮ǰ������Ҳ��֧��`[Child]:[Parent]:[GrandParent]`�����Ķ༶�̳С�

- ������׷�� `+= NewItem`  
	�ں쾯2�ĳЩ�������ͻᱣ���� ini ����ҿ��� Type List��ϰ�������ǳ�֮Ϊע����С�����ע�����ֻ��Ϊռλ������Ϸֱ����ֵ���ʼ����  
    Ares ���ṩ��`+=`���﷨�ǣ�ʹ׷�Ӹ���㡣

	`+=`����������ת��Ϊ`+%d`��������������`+0` `+1`֮��ġ�����ͬ�� ini ʱ����Ҫע�⣬ע����`+=`����û������ظ���

�ƺ����� Phobos Ҳ�����׼̳У����ҵ���д��ʱ��û���õ�������Ȼ��ʧ�ⷽ�濼�ǣ��������Ȼ�� dead project����ȻҲ������ȥ����������顣

### �򵥵�����
```C#
using Chloride.RA2.IniExt;

IniDoc InitIni(FileInfo ini)
{
	IniDoc ret = new();
	ret.Deserialize(ini);
	return ret;
}

var rulesFile = new FileInfo(".\\rulesmd.ini");
var rules = InitIni(rulesFile);
Console.WriteLine(rules["Animations"].Count);
// rules.Serialize(rulesFile, "gb2312"); // buxv "ansi".
```

### �����÷�
��Ϊģ�鵼�� PowerShell Core Ҳ�ǿ��Եġ�**ע�ⲻ�� Windows PowerShell��**  
ֻ�Ƕ�д�ļ�������һЩ�鷳��
- PowerShell ��֧����չ��������Ҫ��ʽ���á�
- PowerShell ��֧��Ĭ�ϲ������������Ĭ�ϲ�������ȫ������ȫ����ָ����
```PowerShell
using namespace Chloride.RA2.IniExt
Import-Module ".\Chloride.RA2.IniExt.dll"

$eg = [IniDoc]::new()
[IniSerializer]::Deserialize($eg, ".\ssks.ini")
# Serialize(this IniDoc doc,
#           FileInfo iniFile,
#           string encoding = "utf-8",
#           string pairing = "=")
[IniSerializer]::Serialize($eg, ".\ssks.ini")
[IniSerializer]::Serialize($eg, ".\ssks_ansi.ini", "gb2312", "=")
[IniSerializer]::Serialize($eg, ".\ssks_with_space.ini", "utf-8", " = ")
```