�ĵ�����2019.04.26������

# CellPhoneDB
***
**��������**

**���ܸ���**

CellPhoneDB��ϸ��ͨѶ���ݿ⣩����һ��������ϸ������-���廥���ԵĴ洢�⡣CellPhoneDB�ɻ��ڵ�ϸ��ת¼�����ݺ����ݿ��м�¼������-���廥����ϵ��ͨ�����������ͬϸ����Ⱥ֮��ķ����໥���ã��Ӷ�Ԥ��ϸ����Ⱥ֮���ͨѶ��ϵ��

**�����ص�**

CellPhoneDB��ͨ��Python������ʽ��ʹ�á�
CellPhoneDB��ϸ��ͨѶ��Ϣ��Դ�������ھ���������ݿ�(UniProt, Ensembl, PDB, the IMEx consortium, IUPHAR����

**�ٷ���ַ**
https://www.cellphonedb.org/

**ʹ��˵��**

���ι��ߣ�Seurat_Cluster
���ι��ߣ�ScBubblePlot
����ʾ����
 


**��������**

**�����ļ�����1 Input Seurat rds File (rds)**
�����������ļ���.rds�ļ���
����˵����
������ϸ��ת¼�������ݵ�rds�ļ��Ǳ��������
rds�ļ����Դ�Seurat_Cluster��Seurat_ReCluster�����ι��߻�ȡ��

**�����ļ�����2 Cluster Rename File (optional)**
ϸ����Ⱥ�������ļ���.txt�ļ���
����˵����
rds�ļ��е�ϸ����Ⱥ��cluster������ͨ��Ϊ���������֡����Ҫ�ĳ��к����ַ�����������ϸ����Ⱥ�������ļ�������Ϊÿ�����У�����Ϊϸ�����ƣ�����Ϊ����ϸ���������ơ����磺
Cell	Cluster
N_AAATCCTGTAACCCTCGGCTACATGCG	MPC
N_AAATCCTGTAACTCATTGACTGAATTC	FC-1
N_AAATCCTGTAAGGACTATAGTTGTTCT	ProFC
ע��
1����ϸ��������ԴΪrds�ļ���
2����Ϊ�滻����ַ�����֧�ֳ����ַ��������֡���ĸ���»��ߡ��Ӻš����š���š��ո�ȡ�
3��ͷ����ȱ��
4ƽ̨Ŀǰ��֧��Unicode�����txt�ļ�

**�����ļ�����3 Cluster Merge File (optional)**
ϸ����Ⱥ�ϲ��ļ���.txt�ļ���
ʹ�����ι��߻�������ͼʱ�����Ҫ����ͬ��ϸ����Ⱥ��Ϊһ�����չʾ�����罫Th1ϸ����Th2ϸ������ΪTϸ������չʾ��������ϸ����Ⱥ�ϲ��ļ�������Ϊÿ�����У�����Ϊ�ϲ�ǰϸ����Ⱥ���ƣ�����Ϊ�ϲ���ϸ����Ⱥ���ơ����磺
Ori_Cluster	Merged_Cluster
pro_B_cell	B_cell
pre_B_cell	B_cell
Th1_cell	T_cell
Th2_cell	T_cell
ע��
1����ϸ����Ⱥ������rds�ļ�����Ϣһ��
2����ϸ����Ⱥ���ƣ�֧�ֳ����ַ��������֡���ĸ���»��ߡ��Ӻš����š���š��ո�ȡ�
3��ͷ����ȱ��
4ƽ̨Ŀǰ��֧��Unicode�����txt�ļ�

**ҳ����ʾ����1 Species**
����
����˵����
Ŀǰ֧���˺�С��

**ҳ����ʾ����2 Threads**
�߳���
����˵����
�����߳���

**ҳ����ʾ����3 Memory(MB)**
�ڴ棨MB��
����˵����
�����ڴ��С

**������**

**����ļ��ṹ**

�ǩ� out (CellPhoneDBԭʼ����ļ�)
��   �ǩ� pvalues.txt (ԭʼpvalues��)
��   �ǩ� means.txt (ԭʼmeans��)
��   �ǩ� pvalues_means.txt (ԭʼpvalue��means���ܱ�)
��   �ǩ� significant_means.txt (ԭʼPֵ������0.05��means��)
�ǩ� pvalues_revise.txt ��������˳���pvalues��
�ǩ� significant_means_revise.txt ��������˳���significant_means��
�ǩ� pvalues_0.05.txt ��������˳����Pֵ������0.05��pvalue��means���ܱ�
�ǩ� BubblePlot (��������ͼ���ߵ���ͼ�����ļ���ÿclusterһ�����4���ļ�)
   �ǩ� 0_Ligand.cluster.txt ��cluster 0��Ϊ����ʱ��cluster�������б�
   �ǩ� 0_Ligand.gene.txt ��cluster 0��Ϊ����ʱ��gene�������б�
   �ǩ� 0_Receptor.cluster.txt ��cluster 0��Ϊ����ʱ��cluster�������б�
   �ǩ� 0_Receptor.gene.txt ��cluster 0��Ϊ����ʱ��gene�������б�
...


**����Pֵ��**

 
˵����
����ÿ�м�¼һ���������廥������Ϣ��ÿ�к������£�
LRtype �����������ͣ�LR��ʾ���������ҷֱ������壨Ligand�������壨Receptor����RR��ʾ�������ӻ�Ϊ�Է�����
interacting_pair ������ϵ�ԣ��û����������»��߼����ʾ
id_cp_interaction CellPhoneDB������ϵID
partner_a ��������A Uniprot ID
partner_b ��������B Uniprot ID
ensembl_a ��������A Ensembl ID
ensembl_b ��������B Ensembl ID
source ������ϵע����Դ
secreted �������Ƿ񺬷����Ե���
is_integrin �������Ƿ�Ϊ������
Pֵ һ�������Ե�Pֵ��������������ϸ����Ⱥ�еĸ����ȡ�����0_1��ʾ�������ӷֱ�����ϸ����Ⱥ0��1
ע��ԭʼPֵ�ļ���������˳��ͳһ��������ͳһ�������߷ֱ�Ϊ�������壬����RR���͵���Ŀ���б��г�������

**����significant_means��**

 

˵����
������Pֵ��ǰ10����ͬ����ͬ�������£�
rank ������ϵ�Ķ����ԣ�ֵԽ�ӽ�0������û�����ϵ��ȫ��ϸ����Ⱥ��Խ���أ�����ĳ����ϸ����Ⱥ���еĻ�����ϵ������ϸ����Ⱥ֮��û�������ϵ��
means ��������������ƽ�����ֵ�ĺͣ�pֵС��0.05��Ӧ��means�ᱻ��������Ϊsignificant_means����ֵԽ���ʾ�û�����ϵǿ��Խǿ��

**pvalues_0.05��**

 
˵����
�������������ű�ǰ10����ͬ������5����ǰ���ű���Ϣ�Ļ��ܡ�����a��b�ǻ���ϸ����Ⱥ���ƣ�P-value/rank/significant_meansȡ���������ű�������pֵС��0.05�����ݡ�

**����ͼ��ͼ�����ļ�**

     
˵����
XXX.gene.txt ������ͼ��ͼ�õĻ���������б�
XXX.cluster.txt ������ͼ��ͼ�õĻ���ϸ����Ⱥ���б�

