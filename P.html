/*
	한글 음절 빈도 조사 프로그램

	입력 파일 : KS 완성형 텍스트 파일(한글을 제외한 문자들은 무시함)
	
	국민대학교 컴퓨터학부 강승식
*/
#include <stdio.h>
#include <string.h>

#define GET_INDEX(c1, c2)	((c1-0xB0)*94 + (c2-0xA1))

/*
	'가나다' 순으로 출력
*/
void put_syl_ABC(FILE *fp, unsigned long count[], unsigned long total)
{
	int i, nsyl=0;
	double percent, accpercent=0.0;

	fprintf(fp, "음절   출현횟수   백분율   누적백분율\n");
	fprintf(fp, "=====================================\n");

	for (i=0; i < 2350; i++) {
		if (count[i]) {	/* 1번 이상 출현한 것만 출력 */
			percent = (double)count[i] / (double)total * 100.0;
			accpercent += percent;
			fprintf(fp, "%c%c %10ld %10.4f %10.4f\n", i/94+0xB0, (i%94)+0xA1,
				count[i], percent, accpercent);
			nsyl++;
		}
	}

	fprintf(fp, "=====================================\n");
	fprintf(fp, "음절 개수 = %ld, 총 음절수 = %ld\n", nsyl, total);
}

/*
	'가나다' 순서 && header 파일 형태로 출력
*/
void put_syl_ABC_header(FILE *fp, unsigned long count[], unsigned long total)
{
	int i, nsyl=0;
	double percent, accpercent=0.0;

	fprintf(fp, "#define N_TOTAL\t%ld\n\n", total);
	fprintf(fp, "unsigned long SYL_FREQ[25][94] = { {\n");

	for (i=0; i < 2350; i++) {
		if (i != 2349) {
			fprintf(fp, "\t%6ld,\t/*%c%c*/\n", count[i], i/94+0xB0, i%94+0xA1);
			if (i % 94 == 93) printf("}, {\n");
		} else fprintf(fp, "\t%6ld\t/*%c%c*/\n} };\n", count[i], i/94+0xB0, i%94+0xA1);
	}
}

double put_one_syllable(FILE *fp, unsigned long count[], int i,
	long total, double accpercent)
{
	double percent;

	percent = (double)count[i] / (double)total * 100.0;
	accpercent += percent;
	fprintf(fp, "%c%c %10ld %10.4f %10.4f\n", i/94+0xB0, (i%94)+0xA1,
		count[i], percent, accpercent);

	return accpercent;
}

/*
	고빈도 순으로 출력
*/
void put_syl_sort(FILE *fp, unsigned long count[], unsigned long total)
{
	int i, j, temp;
	int nsyl=0;
	double accpercent=0.0;
	int index[2350];
	

	for (i = 0; i < 2350; i++) index[i] = i;

	for (i = 0; i < 2350-1; i++) {	/* 고빈도 순으로 sorting */
		for (j = i+1; j < 2350; j++) {
			if (count[index[i]] < count[index[j]]) {
				temp = index[i];
				index[i] = index[j];
				index[j] = temp;
			}
		}
	}

	fprintf(fp, "음절   출현횟수   백분율   누적백분율\n");
	fprintf(fp, "=====================================\n");

	for (i = 0; i < 2350; i++) {
		if (count[index[i]]) {	/* 1번 이상 출현한 것만 출력 */
			accpercent = put_one_syllable(fp, count, index[i], total, accpercent);
			nsyl++;
		}
	}

	fprintf(fp, "=====================================\n");
	fprintf(fp, "음절 개수 = %ld, 총 음절수 = %ld\n", nsyl, total);
}

/*
	고빈도 순서 && header 파일 형태로 출력
*/
void put_syl_sort_header(FILE *fp, unsigned long count[], unsigned long total)
{
	int i, j, temp;
	int nsyl=0;
	double accpercent=0.0;
	int index[2350];
	

	for (i = 0; i < 2350; i++) index[i] = i;
	
	for (i = 0; i < 2350-1; i++) {
		for (j = i+1; j < 2350; j++) {
			if (count[index[i]] < count[index[j]]) {
				temp = index[i];
				index[i] = index[j];
				index[j] = temp;
			}
		}
	}

	fprintf(fp, "#define N_TOTAL\t%ld\n\n", total);
	fprintf(fp, "unsigned SYL_FREQ[25][94][2] = { {\n");

	for (i=0; i < 2350; i++) {
		if (i != 2349) {
			fprintf(fp, "\t{ 0x%x%x, %6ld },\t/*%c%c*/\n",
				index[i]/94+0xB0, index[i]%94+0xA1,
				count[index[i]],
				index[i]/94+0xB0, index[i]%94+0xA1);
			if (i % 94 == 93) printf("}, {\n");
		} else
			fprintf(fp, "\t{ 0x%x%x, %6ld }\t/*%c%c*/\n} };\n",
				index[i]/94+0xB0, index[i]%94+0xA1,
				count[index[i]],
				index[i]/94+0xB0, index[i]%94+0xA1);
	}
}

int main(int argc, char *argv[])
{
	int i, j, k=1, c1, c2, outflag=0;
	unsigned short syl;
	FILE *fpin=stdin, *fpout=stdout;

	unsigned long total_syllable=0;
	unsigned long count[2350] = { 0 };

	if (argc == 1 || !strcmp(argv[1], "-h")) {
		puts("C> run [-s|-s2|-n2] <input-file> <output-file>");
		return 0;
	}

	if (argv[1][0] == '-') {
		k = 2;
		if (!strcmp(argv[1], "-s"))
			outflag = 1;	/* 빈도순으로 소팅 */
		else if (!strcmp(argv[1], "-s2"))
			outflag = 2;	/* 빈도순으로 소팅 && 헤더 파일 형태로 출력 */
		else if (!strcmp(argv[1], "-n2"))
			outflag = 3;	/* 가나다순 && 헤더 파일 형태로 출력 */
	}
	if (k < argc) { if (!(fpin = fopen(argv[k++], "r"))) return -1; }
	if (k < argc) {
		if (fpout = fopen(argv[k], "r")) {
			fclose(fpout);
			fprintf(stderr, "File <%s> exists. Overwrite it? ", argv[k]);
			if (getchar() != 'y') return 0;
		}
		fpout = fopen(argv[k], "w");
	}

	c1 = getc(fpin);
	while(c1 != EOF)
	{
		if (c1 & 0x80) {
			c2 = getc(fpin);
			if (c1 >= 0xB0 && c1 <= 0xC8 &&
				c2 >= 0xA1 && c2 <= 0xFE) {
				syl = GET_INDEX(c1, c2);
				count[syl]++;
				total_syllable++;
			}
		}
		c1 = getc(fpin);
	}

	switch (outflag) {
	case 0:	/* 가나다순으로 출력 */
		put_syl_ABC(fpout, count, total_syllable); break;
	case 1:	/* 빈도순으로 소팅 */
		put_syl_sort(fpout, count, total_syllable); break;
	case 2:	/* 빈도순으로 소팅 && 헤더 파일 형태로 출력 */
		put_syl_sort_header(fpout, count, total_syllable); break;
	case 3:	/* 가나다순 && 헤더 파일 형태로 출력 */
		put_syl_ABC_header(fpout, count, total_syllable); break;
	}

	if (fpin != stdin) fclose(fpin);
	if (fpout!= stdout) fclose(fpout);
	return 0;
}
