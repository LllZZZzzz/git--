Git is a version control system.
Git is free software.
1.
git init -��ʼ�����ؿ�
git config username
git config useremail
git config --global username
git config --global useremail

2.
git log
git log --pretty=oneline
��Ҫ������ʾ���ǣ��㿴����һ������1094adb...����commit id���汾�ţ���
��SVN��һ����Git��commit id����1��2��3�������������֣�����һ��SHA1���������һ���ǳ�������֣�
��ʮ�����Ʊ�ʾ�������㿴����commit id���ҵĿ϶���һ���������Լ���Ϊ׼��Ϊʲôcommit id��Ҫ����ôһ�����ֱ�ʾ�أ�
��ΪGit�Ƿֲ�ʽ�İ汾����ϵͳ���������ǻ�Ҫ�о�������ͬһ���汾���﹤���������Ҷ���1��2��3������Ϊ�汾�ţ��ǿ϶��ͳ�ͻ�ˡ�

3.
git reset --hard HEAD^ ����һ��
git reset --hard commit_id
git log �鿴�ύ��ʷ �Ա�ȷ�����˵��ĸ��汾
git reflog (-- file) �鿴������ʷ �Ա�ȷ��Ҫ�ص�δ�����ĸ��汾
 
4.
ΪʲôGit�������汾����ϵͳ��Ƶ����㣬��ΪGit���ٲ���������޸ģ������ļ���
git diff HEAD������Բ鿴�������Ͱ汾���������°汾������

5.
git checkout -- file���Զ������������޸�
��֮������������ļ��ص����һ��git commit��git addʱ��״̬��
git reset HEAD -- file���԰��ݴ������޸ĳ�������unstage�������·Żع�������
�Ѿ��ύ�˲����ʵ��޸ĵ��汾��ʱ����Ҫ���������ύ���ο��汾����һ�ڣ�����ǰ����û�����͵�Զ�̿⡣

6.
git rmɾ�����������ݴ����ļ�������git commitɾ�����ؿ��ļ�
����git reset --hard �ָ����ؿ���ļ�
����git ckeckout -- file�ָ��������ļ�

7.
���ȱ���֪���ֿ�ĵ�ַ��Ȼ��ʹ��git clone�����¡��
Git֧�ֶ���Э�飬����https����ͨ��ssh֧�ֵ�ԭ��gitЭ���ٶ���졣
GitHub�����ĵ�ַ��ֹһ������������https://github.com/michaelliao/gitskills.git�����ĵ�ַ��
ʵ���ϣ�Git֧�ֶ���Э�飬Ĭ�ϵ�git://ʹ��ssh����Ҳ����ʹ��https������Э�顣
ʹ��https�����ٶ������⣬���и������鷳��ÿ�����Ͷ�����������
������ĳЩֻ����http�˿ڵĹ�˾�ڲ����޷�ʹ��sshЭ���ֻ����https��