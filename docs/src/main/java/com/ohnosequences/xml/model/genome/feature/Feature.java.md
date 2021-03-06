
 * Copyright (C) 2010-2012  "Oh no sequences!"
 *
 * This is free software: you can redistribute it and/or modify
 * it under the terms of the GNU Affero General Public License as
 * published by the Free Software Foundation, either version 3 of the
 * License, or (at your option) any later version.
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU Affero General Public License for more details.
 * You should have received a copy of the GNU Affero General Public License
 * along with this program.  If not, see <http://www.gnu.org/licenses/>


```java
package com.ohnosequences.xml.model.genome.feature;

import com.ohnosequences.xml.model.pal.PalindromicityResultXML;
import com.ohnosequences.xml.api.model.XMLElement;
import com.ohnosequences.xml.api.model.XMLElementException;
import org.jdom2.Element;

/**
 *
 * @author ppareja
 */
public class Feature extends XMLElement implements Comparable<Feature>{

    public static final String POSITIVE_STRAND = "+";
    public static final String NEGATIVE_STRAND = "-";

    public static final String ID_TAG_NAME = "id";
    public static final String NAME_TAG_NAME = "name";
    public static final String BEGIN_TAG_NAME = "begin";
    public static final String SEQUENCE_TAG_NAME = "sequence";
    public static final String STRAND_TAG_NAME = "strand";
    public static final String LEADING_STRAND_TAG_NAME = "leading_strand";
    public static final String LENGTH_TAG_NAME = "length";
    public static final String END_TAG_NAME = "end";
    public static final String ERROR_TAG_NAME = "error";
    
    public static final String TOTAL_A_TAG_NAME = "total_a";
    public static final String TOTAL_C_TAG_NAME = "total_c";
    public static final String TOTAL_G_TAG_NAME = "total_g";
    public static final String TOTAL_T_TAG_NAME = "total_t";
    public static final String TOTAL_OTHER_TAG_NAME = "total_other";

    public static final String A_IN_1_TAG_NAME = "a_in_1";
    public static final String C_IN_1_TAG_NAME = "c_in_1";
    public static final String G_IN_1_TAG_NAME = "g_in_1";
    public static final String T_IN_1_TAG_NAME = "t_in_1";
    public static final String OTHER_IN_1_TAG_NAME = "other_in_1";

    public static final String A_IN_2_TAG_NAME = "a_in_2";
    public static final String C_IN_2_TAG_NAME = "c_in_2";
    public static final String G_IN_2_TAG_NAME = "g_in_2";
    public static final String T_IN_2_TAG_NAME = "t_in_2";
    public static final String OTHER_IN_2_TAG_NAME = "other_in_2";

    public static final String A_IN_3_TAG_NAME = "a_in_3";
    public static final String C_IN_3_TAG_NAME = "c_in_3";
    public static final String G_IN_3_TAG_NAME = "g_in_3";
    public static final String T_IN_3_TAG_NAME = "t_in_3";
    public static final String OTHER_IN_3_TAG_NAME = "other_in_3";

    public static final String A_IN_SILENT_3_TAG_NAME = "a_in_silent_3";
    public static final String C_IN_SILENT_3_TAG_NAME = "c_in_silent_3";
    public static final String G_IN_SILENT_3_TAG_NAME = "g_in_silent_3";
    public static final String T_IN_SILENT_3_TAG_NAME = "t_in_silent_3";
    public static final String OTHER_IN_SILENT_3_TAG_NAME = "other_in_silent_3";

    //----------PALINDROMICITY-----------
    public static final String ODD_AXIS_PALINDROMICITY_TAG_NAME = "odd_axis_pal";
    public static final String EVEN_AXIS_PALINDROMICITY_TAG_NAME = "even_axis_pal";
    public static final String MAX_WORD_LENGTH_EVEN_AXIS_PALINDROMICITY_TAG_NAME = "mwl_even_axis_pal";
    public static final String MAX_WORD_LENGTH_ODD_AXIS_PALINDROMICITY_TAG_NAME = "mwl_odd_axis_pal";


    public Feature(Element elem) throws XMLElementException{
        super(elem);
    }
    public Feature(String value) throws Exception{
        super(value);
    }

    public void appendToSequence(String value){
        Element seqElem = root.getChild(SEQUENCE_TAG_NAME);
        if(seqElem == null){
            root.addContent(new Element(SEQUENCE_TAG_NAME));
            seqElem = root.getChild(SEQUENCE_TAG_NAME);
        }
        seqElem.setText(seqElem.getText()+value);
    }

    //----------------GETTERS---------------------
    public String getId(){  return getNodeText(ID_TAG_NAME); }
    public String getFeatureName(){    return getNodeText(NAME_TAG_NAME);}
    public String getSequence(){    return getNodeText(SEQUENCE_TAG_NAME);}
    public String getStrand(){  return getNodeText(STRAND_TAG_NAME);}
    public boolean getLeadingStrand(){  return Boolean.parseBoolean(getNodeText(LEADING_STRAND_TAG_NAME));}
    public int getLength() {    return Integer.parseInt(getNodeText(LENGTH_TAG_NAME));}
    public int getBegin(){  return Integer.parseInt(getNodeText(BEGIN_TAG_NAME)); }
    public int getEnd(){  return Integer.parseInt(getNodeText(END_TAG_NAME)); }
    public String getError(){   return getNodeText(ERROR_TAG_NAME);}

    public float getTotalA(){ return Float.parseFloat(getNodeText(TOTAL_A_TAG_NAME));}
    public float getTotalC(){ return Float.parseFloat(getNodeText(TOTAL_C_TAG_NAME));}
    public float getTotalG(){ return Float.parseFloat(getNodeText(TOTAL_G_TAG_NAME));}
    public float getTotalT(){ return Float.parseFloat(getNodeText(TOTAL_T_TAG_NAME));}
    public float getTotalOther(){   return Float.parseFloat(getNodeText(TOTAL_OTHER_TAG_NAME));}

    public float getAIn1(){   return Float.parseFloat(getNodeText(A_IN_1_TAG_NAME));}
    public float getCIn1(){   return Float.parseFloat(getNodeText(C_IN_1_TAG_NAME));}
    public float getGIn1(){   return Float.parseFloat(getNodeText(G_IN_1_TAG_NAME));}
    public float getTIn1(){   return Float.parseFloat(getNodeText(T_IN_1_TAG_NAME));}
    public float getOtherIn1(){ return Float.parseFloat(getNodeText(OTHER_IN_1_TAG_NAME));}

    public float getAIn2(){   return Float.parseFloat(getNodeText(A_IN_2_TAG_NAME));}
    public float getCIn2(){   return Float.parseFloat(getNodeText(C_IN_2_TAG_NAME));}
    public float getGIn2(){   return Float.parseFloat(getNodeText(G_IN_2_TAG_NAME));}
    public float getTIn2(){   return Float.parseFloat(getNodeText(T_IN_2_TAG_NAME));}
    public float getOtherIn2(){ return Float.parseFloat(getNodeText(OTHER_IN_2_TAG_NAME));}

    public float getAIn3(){   return Float.parseFloat(getNodeText(A_IN_3_TAG_NAME));}
    public float getCIn3(){   return Float.parseFloat(getNodeText(C_IN_3_TAG_NAME));}
    public float getGIn3(){   return Float.parseFloat(getNodeText(G_IN_3_TAG_NAME));}
    public float getTIn3(){   return Float.parseFloat(getNodeText(T_IN_3_TAG_NAME));}
    public float getOtherIn3(){ return Float.parseFloat(getNodeText(OTHER_IN_3_TAG_NAME));}

    public float getAInSilent3(){   return Float.parseFloat(getNodeText(A_IN_SILENT_3_TAG_NAME));}
    public float getCInSilent3(){   return Float.parseFloat(getNodeText(C_IN_SILENT_3_TAG_NAME));}
    public float getGInSilent3(){   return Float.parseFloat(getNodeText(G_IN_SILENT_3_TAG_NAME));}
    public float getTInSilent3(){   return Float.parseFloat(getNodeText(T_IN_SILENT_3_TAG_NAME));}
    public float getOtherInSilent3(){   return Float.parseFloat(getNodeText(OTHER_IN_SILENT_3_TAG_NAME));}

    public PalindromicityResultXML getOddAxisPalindromicityResult() throws XMLElementException{
        Element elem = root.getChild(ODD_AXIS_PALINDROMICITY_TAG_NAME);
        if(elem == null){
            return null;
        }else{
            Element palResult = elem.getChild(PalindromicityResultXML.TAG_NAME);
            if(palResult == null){
                return null;
            }else{
                return new PalindromicityResultXML(palResult);
            }
        }
    }
    public PalindromicityResultXML getEvenAxisPalindromicityResult() throws XMLElementException{
        Element elem = root.getChild(EVEN_AXIS_PALINDROMICITY_TAG_NAME);
        if(elem == null){
            return null;
        }else{
            Element palResult = elem.getChild(PalindromicityResultXML.TAG_NAME);
            if(palResult == null){
                return null;
            }else{
                return new PalindromicityResultXML(palResult);
            }
        }
    }
    public PalindromicityResultXML getMaxWordLengthEvenAxisPalindromicityResult() throws XMLElementException{
        Element elem = root.getChild(MAX_WORD_LENGTH_EVEN_AXIS_PALINDROMICITY_TAG_NAME);
        if(elem == null){
            return null;
        }else{
            Element palResult = elem.getChild(PalindromicityResultXML.TAG_NAME);
            if(palResult == null){
                return null;
            }else{
                return new PalindromicityResultXML(palResult);
            }
        }
    }
    public PalindromicityResultXML getMaxWordLengthOddAxisPalindromicityResult() throws XMLElementException{
        Element elem = root.getChild(MAX_WORD_LENGTH_ODD_AXIS_PALINDROMICITY_TAG_NAME);
        if(elem == null){
            return null;
        }else{
            Element palResult = elem.getChild(PalindromicityResultXML.TAG_NAME);
            if(palResult == null){
                return null;
            }else{
                return new PalindromicityResultXML(palResult);
            }
        }
    }


    //----------------SETTERS---------------------
    public void setId(String value){    setNodeText(ID_TAG_NAME,value);}
    public void setFeatureName(String value){  setNodeText(NAME_TAG_NAME, value);}
    public void setSequence(String value){  setNodeText(SEQUENCE_TAG_NAME,value);}
    public void setStrand(String value){    setNodeText(STRAND_TAG_NAME,value);}
    public void setLeadingStrand(boolean value){    setNodeText(LEADING_STRAND_TAG_NAME, String.valueOf(value));}
    public void setLength(int value){   setNodeText(LENGTH_TAG_NAME,String.valueOf(value));}
    public void setBegin(int value){    setNodeText(BEGIN_TAG_NAME,String.valueOf(value));}
    public void setEnd(int value){    setNodeText(END_TAG_NAME,String.valueOf(value));}
    public void setError(String value){ setNodeText(ERROR_TAG_NAME,value);}

    public void setTotalA(float value){   setNodeText(TOTAL_A_TAG_NAME, String.valueOf(value));}
    public void setTotalC(float value){   setNodeText(TOTAL_C_TAG_NAME, String.valueOf(value));}
    public void setTotalG(float value){   setNodeText(TOTAL_G_TAG_NAME, String.valueOf(value));}
    public void setTotalT(float value){   setNodeText(TOTAL_T_TAG_NAME, String.valueOf(value));}
    public void setTotalOther(float value){ setNodeText(TOTAL_OTHER_TAG_NAME, String.valueOf(value));}

    public void setAIn1(float value){     setNodeText(A_IN_1_TAG_NAME,String.valueOf(value));}
    public void setCIn1(float value){     setNodeText(C_IN_1_TAG_NAME,String.valueOf(value));}
    public void setGIn1(float value){     setNodeText(G_IN_1_TAG_NAME,String.valueOf(value));}
    public void setTIn1(float value){     setNodeText(T_IN_1_TAG_NAME,String.valueOf(value));}
    public void setOtherIn1(float value){   setNodeText(OTHER_IN_1_TAG_NAME,String.valueOf(value));}

    public void setAIn2(float value){     setNodeText(A_IN_2_TAG_NAME,String.valueOf(value));}
    public void setCIn2(float value){     setNodeText(C_IN_2_TAG_NAME,String.valueOf(value));}
    public void setGIn2(float value){     setNodeText(G_IN_2_TAG_NAME,String.valueOf(value));}
    public void setTIn2(float value){     setNodeText(T_IN_2_TAG_NAME,String.valueOf(value));}
    public void setOtherIn2(float value){   setNodeText(OTHER_IN_2_TAG_NAME,String.valueOf(value));}

    public void setAIn3(float value){     setNodeText(A_IN_3_TAG_NAME,String.valueOf(value));}
    public void setCIn3(float value){     setNodeText(C_IN_3_TAG_NAME,String.valueOf(value));}
    public void setGIn3(float value){     setNodeText(G_IN_3_TAG_NAME,String.valueOf(value));}
    public void setTIn3(float value){     setNodeText(T_IN_3_TAG_NAME,String.valueOf(value));}
    public void setOtherIn3(float value){   setNodeText(OTHER_IN_3_TAG_NAME, String.valueOf(value));}

    public void setAInSilent3(float value){   setNodeText(A_IN_SILENT_3_TAG_NAME,String.valueOf(value));}
    public void setCInSilent3(float value){   setNodeText(C_IN_SILENT_3_TAG_NAME,String.valueOf(value));}
    public void setGInSilent3(float value){   setNodeText(G_IN_SILENT_3_TAG_NAME,String.valueOf(value));}
    public void setTInSilent3(float value){   setNodeText(T_IN_SILENT_3_TAG_NAME,String.valueOf(value));}
    public void setOtherInSilent3(float value){  setNodeText(OTHER_IN_SILENT_3_TAG_NAME, String.valueOf(value));}

    public void setOddAxisPalindromicityResult(PalindromicityResultXML result){
        root.removeChildren(ODD_AXIS_PALINDROMICITY_TAG_NAME);
        Element elem = new Element(ODD_AXIS_PALINDROMICITY_TAG_NAME);
        elem.addContent(result.getRoot());
        root.addContent(elem);
    }
    public void setEvenAxisPalindromicityResult(PalindromicityResultXML result){
        root.removeChildren(EVEN_AXIS_PALINDROMICITY_TAG_NAME);
        Element elem = new Element(EVEN_AXIS_PALINDROMICITY_TAG_NAME);
        elem.addContent(result.getRoot());
        root.addContent(elem);
    }
    public void setMaxWordLengthOddAxisPalindromicityResult(PalindromicityResultXML result){
        root.removeChildren(MAX_WORD_LENGTH_ODD_AXIS_PALINDROMICITY_TAG_NAME);
        Element elem = new Element(MAX_WORD_LENGTH_ODD_AXIS_PALINDROMICITY_TAG_NAME);
        elem.addContent(result.getRoot());
        root.addContent(elem);
    }
    public void setMaxWordLengthEvenAxisPalindromicityResult(PalindromicityResultXML result){
        root.removeChildren(MAX_WORD_LENGTH_EVEN_AXIS_PALINDROMICITY_TAG_NAME);
        Element elem = new Element(MAX_WORD_LENGTH_EVEN_AXIS_PALINDROMICITY_TAG_NAME);
        elem.addContent(result.getRoot());
        root.addContent(elem);
    }


    @Override
    public int compareTo(Feature feature) {
        if(feature.getBegin() == this.getBegin()){
            return 0;
        }else if(this.getBegin() < feature.getBegin() ){
            return -1;
        }else{
            return 1;
        }
    }

    public void removeSequence(){
        root.removeChildren(SEQUENCE_TAG_NAME);
    }

    
    


}

```




[main/java/com/ohnosequences/BioinfoUtil.java]: ../../../../BioinfoUtil.java.md
[main/java/com/ohnosequences/util/BitOperations.java]: ../../../../util/BitOperations.java.md
[main/java/com/ohnosequences/util/blast/BlastExporter.java]: ../../../../util/blast/BlastExporter.java.md
[main/java/com/ohnosequences/util/blast/BlastSubset.java]: ../../../../util/blast/BlastSubset.java.md
[main/java/com/ohnosequences/util/CodonUtil.java]: ../../../../util/CodonUtil.java.md
[main/java/com/ohnosequences/util/Entry.java]: ../../../../util/Entry.java.md
[main/java/com/ohnosequences/util/Executable.java]: ../../../../util/Executable.java.md
[main/java/com/ohnosequences/util/ExecuteFromFile.java]: ../../../../util/ExecuteFromFile.java.md
[main/java/com/ohnosequences/util/fasta/FastaSubSeq.java]: ../../../../util/fasta/FastaSubSeq.java.md
[main/java/com/ohnosequences/util/fasta/FastaUtil.java]: ../../../../util/fasta/FastaUtil.java.md
[main/java/com/ohnosequences/util/fasta/MultifastaSelector.java]: ../../../../util/fasta/MultifastaSelector.java.md
[main/java/com/ohnosequences/util/fasta/SearchFastaHeaders.java]: ../../../../util/fasta/SearchFastaHeaders.java.md
[main/java/com/ohnosequences/util/fasta/SearchFastaSequence.java]: ../../../../util/fasta/SearchFastaSequence.java.md
[main/java/com/ohnosequences/util/file/FileUtil.java]: ../../../../util/file/FileUtil.java.md
[main/java/com/ohnosequences/util/file/FnaFileFilter.java]: ../../../../util/file/FnaFileFilter.java.md
[main/java/com/ohnosequences/util/file/GenomeFilesParser.java]: ../../../../util/file/GenomeFilesParser.java.md
[main/java/com/ohnosequences/util/file/PttFileFilter.java]: ../../../../util/file/PttFileFilter.java.md
[main/java/com/ohnosequences/util/file/RntFileFilter.java]: ../../../../util/file/RntFileFilter.java.md
[main/java/com/ohnosequences/util/genbank/GBCommon.java]: ../../../../util/genbank/GBCommon.java.md
[main/java/com/ohnosequences/util/gephi/GephiExporter.java]: ../../../../util/gephi/GephiExporter.java.md
[main/java/com/ohnosequences/util/gephi/GexfToDotExporter.java]: ../../../../util/gephi/GexfToDotExporter.java.md
[main/java/com/ohnosequences/util/go/GOExporter.java]: ../../../../util/go/GOExporter.java.md
[main/java/com/ohnosequences/util/model/Feature.java]: ../../../../util/model/Feature.java.md
[main/java/com/ohnosequences/util/model/Intergenic.java]: ../../../../util/model/Intergenic.java.md
[main/java/com/ohnosequences/util/model/PalindromicityResult.java]: ../../../../util/model/PalindromicityResult.java.md
[main/java/com/ohnosequences/util/ncbi/TaxonomyLoader.java]: ../../../../util/ncbi/TaxonomyLoader.java.md
[main/java/com/ohnosequences/util/oric/OricDataRetriever.java]: ../../../../util/oric/OricDataRetriever.java.md
[main/java/com/ohnosequences/util/Pair.java]: ../../../../util/Pair.java.md
[main/java/com/ohnosequences/util/pal/PalindromicityAnalyzer.java]: ../../../../util/pal/PalindromicityAnalyzer.java.md
[main/java/com/ohnosequences/util/security/MD5.java]: ../../../../util/security/MD5.java.md
[main/java/com/ohnosequences/util/seq/SeqUtil.java]: ../../../../util/seq/SeqUtil.java.md
[main/java/com/ohnosequences/util/statistics/StatisticalValues.java]: ../../../../util/statistics/StatisticalValues.java.md
[main/java/com/ohnosequences/util/uniprot/UniprotProteinRetreiver.java]: ../../../../util/uniprot/UniprotProteinRetreiver.java.md
[main/java/com/ohnosequences/xml/api/interfaces/IAttribute.java]: ../../../api/interfaces/IAttribute.java.md
[main/java/com/ohnosequences/xml/api/interfaces/IElement.java]: ../../../api/interfaces/IElement.java.md
[main/java/com/ohnosequences/xml/api/interfaces/INameSpace.java]: ../../../api/interfaces/INameSpace.java.md
[main/java/com/ohnosequences/xml/api/interfaces/IXmlThing.java]: ../../../api/interfaces/IXmlThing.java.md
[main/java/com/ohnosequences/xml/api/interfaces/package-info.java]: ../../../api/interfaces/package-info.java.md
[main/java/com/ohnosequences/xml/api/model/NameSpace.java]: ../../../api/model/NameSpace.java.md
[main/java/com/ohnosequences/xml/api/model/package-info.java]: ../../../api/model/package-info.java.md
[main/java/com/ohnosequences/xml/api/model/XMLAttribute.java]: ../../../api/model/XMLAttribute.java.md
[main/java/com/ohnosequences/xml/api/model/XMLElement.java]: ../../../api/model/XMLElement.java.md
[main/java/com/ohnosequences/xml/api/model/XMLElementException.java]: ../../../api/model/XMLElementException.java.md
[main/java/com/ohnosequences/xml/api/util/XMLUtil.java]: ../../../api/util/XMLUtil.java.md
[main/java/com/ohnosequences/xml/model/Annotation.java]: ../../Annotation.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jNodeIndexXML.java]: ../../bio4j/Bio4jNodeIndexXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jNodeXML.java]: ../../bio4j/Bio4jNodeXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jPropertyXML.java]: ../../bio4j/Bio4jPropertyXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jRelationshipIndexXML.java]: ../../bio4j/Bio4jRelationshipIndexXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jRelationshipXML.java]: ../../bio4j/Bio4jRelationshipXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/UniprotDataXML.java]: ../../bio4j/UniprotDataXML.java.md
[main/java/com/ohnosequences/xml/model/BlastOutput.java]: ../../BlastOutput.java.md
[main/java/com/ohnosequences/xml/model/BlastOutputParam.java]: ../../BlastOutputParam.java.md
[main/java/com/ohnosequences/xml/model/Codon.java]: ../../Codon.java.md
[main/java/com/ohnosequences/xml/model/ContigXML.java]: ../../ContigXML.java.md
[main/java/com/ohnosequences/xml/model/cufflinks/CuffLinksElement.java]: ../../cufflinks/CuffLinksElement.java.md
[main/java/com/ohnosequences/xml/model/embl/EmblXML.java]: ../../embl/EmblXML.java.md
[main/java/com/ohnosequences/xml/model/Frameshift.java]: ../../Frameshift.java.md
[main/java/com/ohnosequences/xml/model/Gap.java]: ../../Gap.java.md
[main/java/com/ohnosequences/xml/model/gb/GenBankXML.java]: ../../gb/GenBankXML.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/Feature.java]: Feature.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/Intergenic.java]: Intergenic.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/MisRNA.java]: MisRNA.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/ORF.java]: ORF.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/RNA.java]: RNA.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/RRNA.java]: RRNA.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/TRNA.java]: TRNA.java.md
[main/java/com/ohnosequences/xml/model/genome/GenomeElement.java]: ../GenomeElement.java.md
[main/java/com/ohnosequences/xml/model/gexf/AttributesXML.java]: ../../gexf/AttributesXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/AttributeXML.java]: ../../gexf/AttributeXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/AttValuesXML.java]: ../../gexf/AttValuesXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/AttValueXML.java]: ../../gexf/AttValueXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/EdgesXML.java]: ../../gexf/EdgesXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/EdgeXML.java]: ../../gexf/EdgeXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/GexfXML.java]: ../../gexf/GexfXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/GraphXML.java]: ../../gexf/GraphXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/NodesXML.java]: ../../gexf/NodesXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/NodeXML.java]: ../../gexf/NodeXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/SpellsXML.java]: ../../gexf/SpellsXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/SpellXML.java]: ../../gexf/SpellXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/viz/VizColorXML.java]: ../../gexf/viz/VizColorXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/viz/VizPositionXML.java]: ../../gexf/viz/VizPositionXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/viz/VizSizeXML.java]: ../../gexf/viz/VizSizeXML.java.md
[main/java/com/ohnosequences/xml/model/go/GoAnnotationXML.java]: ../../go/GoAnnotationXML.java.md
[main/java/com/ohnosequences/xml/model/go/GOSlimXML.java]: ../../go/GOSlimXML.java.md
[main/java/com/ohnosequences/xml/model/go/GoTermXML.java]: ../../go/GoTermXML.java.md
[main/java/com/ohnosequences/xml/model/go/SlimSetXML.java]: ../../go/SlimSetXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/DataXML.java]: ../../graphml/DataXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/EdgeXML.java]: ../../graphml/EdgeXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/GraphmlXML.java]: ../../graphml/GraphmlXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/GraphXML.java]: ../../graphml/GraphXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/KeyXML.java]: ../../graphml/KeyXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/NodeXML.java]: ../../graphml/NodeXML.java.md
[main/java/com/ohnosequences/xml/model/Hit.java]: ../../Hit.java.md
[main/java/com/ohnosequences/xml/model/Hsp.java]: ../../Hsp.java.md
[main/java/com/ohnosequences/xml/model/HspSet.java]: ../../HspSet.java.md
[main/java/com/ohnosequences/xml/model/Iteration.java]: ../../Iteration.java.md
[main/java/com/ohnosequences/xml/model/logs/LogRecordXML.java]: ../../logs/LogRecordXML.java.md
[main/java/com/ohnosequences/xml/model/metagenomics/ReadResultXML.java]: ../../metagenomics/ReadResultXML.java.md
[main/java/com/ohnosequences/xml/model/metagenomics/ReadXML.java]: ../../metagenomics/ReadXML.java.md
[main/java/com/ohnosequences/xml/model/metagenomics/SampleXML.java]: ../../metagenomics/SampleXML.java.md
[main/java/com/ohnosequences/xml/model/MetagenomicsDataXML.java]: ../../MetagenomicsDataXML.java.md
[main/java/com/ohnosequences/xml/model/mg7/MG7DataXML.java]: ../../mg7/MG7DataXML.java.md
[main/java/com/ohnosequences/xml/model/mg7/ReadResultXML.java]: ../../mg7/ReadResultXML.java.md
[main/java/com/ohnosequences/xml/model/mg7/SampleXML.java]: ../../mg7/SampleXML.java.md
[main/java/com/ohnosequences/xml/model/ncbi/NCBITaxonomyNodeXML.java]: ../../ncbi/NCBITaxonomyNodeXML.java.md
[main/java/com/ohnosequences/xml/model/oric/Oric.java]: ../../oric/Oric.java.md
[main/java/com/ohnosequences/xml/model/Overlap.java]: ../../Overlap.java.md
[main/java/com/ohnosequences/xml/model/pal/PalindromicityResultXML.java]: ../../pal/PalindromicityResultXML.java.md
[main/java/com/ohnosequences/xml/model/pg/Primer.java]: ../../pg/Primer.java.md
[main/java/com/ohnosequences/xml/model/PredictedGene.java]: ../../PredictedGene.java.md
[main/java/com/ohnosequences/xml/model/PredictedGenes.java]: ../../PredictedGenes.java.md
[main/java/com/ohnosequences/xml/model/PredictedRna.java]: ../../PredictedRna.java.md
[main/java/com/ohnosequences/xml/model/PredictedRnas.java]: ../../PredictedRnas.java.md
[main/java/com/ohnosequences/xml/model/uniprot/ArticleXML.java]: ../../uniprot/ArticleXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/CommentXML.java]: ../../uniprot/CommentXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/FeatureXML.java]: ../../uniprot/FeatureXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/InterproXML.java]: ../../uniprot/InterproXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/IsoformXML.java]: ../../uniprot/IsoformXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/KeywordXML.java]: ../../uniprot/KeywordXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/ProteinXML.java]: ../../uniprot/ProteinXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/SubcellularLocationXML.java]: ../../uniprot/SubcellularLocationXML.java.md
[main/java/com/ohnosequences/xml/model/util/Argument.java]: ../../util/Argument.java.md
[main/java/com/ohnosequences/xml/model/util/Arguments.java]: ../../util/Arguments.java.md
[main/java/com/ohnosequences/xml/model/util/Error.java]: ../../util/Error.java.md
[main/java/com/ohnosequences/xml/model/util/Execution.java]: ../../util/Execution.java.md
[main/java/com/ohnosequences/xml/model/util/FlexXMLWrapperClassCreator.java]: ../../util/FlexXMLWrapperClassCreator.java.md
[main/java/com/ohnosequences/xml/model/util/ScheduledExecutions.java]: ../../util/ScheduledExecutions.java.md
[main/java/com/ohnosequences/xml/model/util/XMLWrapperClass.java]: ../../util/XMLWrapperClass.java.md
[main/java/com/ohnosequences/xml/model/util/XMLWrapperClassCreator.java]: ../../util/XMLWrapperClassCreator.java.md
[main/java/com/ohnosequences/xml/model/wip/Region.java]: ../../wip/Region.java.md
[main/java/com/ohnosequences/xml/model/wip/WipPosition.java]: ../../wip/WipPosition.java.md
[main/java/com/ohnosequences/xml/model/wip/WipResult.java]: ../../wip/WipResult.java.md