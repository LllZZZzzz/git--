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
git reflog �鿴������ʷ �Ա�ȷ��Ҫ�ص�δ�����ĸ��汾
 4.
123