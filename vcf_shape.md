# VCF 형태

### Basic info
- TSV(Tab-seperated values)
- UTF-8 incoding
- `</br>` by LF(“\n”) or CR+LF(“\r\n”)

### Line type
1. ##으로 시작하는 메타 정보(meta-information) 라인: [Meta-information lines](#meta-information-lines)
2. #으로 시작하는 한 줄의 헤더 라인: [Header line](#header-line)
3. 유전자 단위의 변이 별로 한 줄을 이루는 데이터 라인: [Data line](#data-line)

### Meta-information lines
- VCF의 정보를 파싱하기 위해서, 그리고 VCF의 binary 형식인 BCF로의 변환

**File Format: `##fileformat`**
- VCF 파일의 버전

**Information field format:`##INFO`**
- line info field의 format

**Filter field format: `##FILTER`**
- 변이 검사 퀄리티를 나타내는 FILTER 필드

**Individual format field format: `##FORMAT`**
- genotype 별 데이터가 나오는데, 이 때 여기에 어떤 데이터가 어떤 format으로 들어가 있는지

### Header line
- 데이터 라인에 어떤 필드들이 있는지 알려주는 라인

### Data line
**Info**
- 각 변이의 추가 정보를 제공하는 필드

**CHROM**
- chromosome: 변이가 위치하는 염색체 번호

**POS**
- position: 변이의 염색체 내 위치

**ID**
- identifier: 유전자 ID. 일반적으로 dbSNP 내에서의 유전자 ID를 사용
- 만약 ID를 찾을 수 없는 경우 ‘.’이 입력됩니다.

**REF**
- reference base(s): 해당 변이의 위치에서 정상이라고 판단되는 원래 base 시퀀스
- 길이 1 이상의 정상 bases가 나열 : `A, C, G, T, N`로 이루어진 문자열

**ALT**
- alternate base(s): 유전자 검사에서 나온, reference bases와 다른 유전자, 즉 변이 bases

**QUAL**
- quality: Phred 품질 점수

**FILTER**
- filter status: 품질 점수에 따른 신뢰도
- 특정 신뢰도(filter)를 만족하는 경우 ‘PASS’로 표시되고, 특정 신뢰도를 만족하지 못하는 경우 “q10;s50”와 같이 만족하지 못한 filter에 대한 정보가 표시
- 만약 filter가 적용되지 않은 경우 ‘.’으로 표시됩니다.

**INFO**
- additional information: 변이에 대한 추가 정보를 담고 있는 필드
- 세미콜론(;)으로 구분된 여러 데이터가 key=value[,value] 형태로 나열된 문자열
- 각 필드에 대한 설명은 meta-information에 정의

**FORMAT**
- genotype fields format: 뒤에 나오는 genotype fields에 어떤 순서대로 데이터가 나올지 형태를 알려주는 필드
- 콜론(:)으로 구분된 테이터 key들이 나열
- 각 필드에 대한 설명은 meta-information에 정의


**Genotype fields**
- 샘플 별로 변이에 대한 추가 정보를 제공
- 앞의 FORMAT 필드에서 표시한대로 각 데이터를 콜론(:)으로 구분해서 나열

