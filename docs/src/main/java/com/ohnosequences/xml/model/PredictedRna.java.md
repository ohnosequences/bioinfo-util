
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
package com.ohnosequences.xml.model;

import com.ohnosequences.xml.api.model.XMLElement;
import com.ohnosequences.xml.api.model.XMLElementException;
import java.util.ArrayList;
import java.util.List;
import org.jdom2.Element;

/**
 *
 * @author <a href="mailto:ppareja@ohnosequences.com">Pablo Pareja-Tobes</a>
 */
public class PredictedRna extends XMLElement implements Comparable<PredictedRna>{

    public static final String TAG_NAME = "predicted_rna";

    public static final String ID_TAG_NAME = "id";
    public static final String SEQUENCE_TAG_NAME = "sequence";
    public static final String EVALUE_TAG_NAME = "evalue";
    public static final String CONTIG_ID_TAG_NAME = "contig_id";
    public static final String ANNOTATION_UNIPROT_ID_TAG_NAME = "annotation_uniprot_id";
    public static final String ANNOTATION_SCORE_EVALUE_TAG_NAME = "annotation_score_evalue";
    public static final String BLAST_HIT_START_TAG_NAME = "blast_hit_start";
    public static final String BLAST_HIT_END_TAG_NAME = "blast_hit_end";
    public static final String DNA_SEQUENCE_TAG_NAME = "dna_sequence";
    public static final String STRAND_TAG_NAME = "strand";
    public static final String HIT_DEF_TAG_NAME = "hit_def";
    public static final String RNA_NAME_TAG_NAME = "name";

    public static final String POSITIVE_STRAND = "+";
    public static final String NEGATIVE_STRAND = "-";

    public static final String START_POSITION_TAG_NAME = "start_position";
    public static final String START_IS_CANONICAL_TAG_NAME = "start_is_canonical";
    public static final String END_POSITION_TAG_NAME = "end_position";
    public static final String END_IS_CANONICAL_TAG_NAME = "end_is_canonical";

    public static final String START_CODON_TAG_NAME = "start_codon";
    public static final String STOP_CODON_TAG_NAME = "stop_codon";

    public static final String EXTRA_STOP_CODONS_TAG_NAME = "extra_stop_codons";
    public static final String FRAME_SHIFTS_TAG_NAME = "frameshifts";


    //--------------POSSIBLE STATUS------------
    public static final String STATUS_DISMISSED = "dismissed";
    public static final String STATUS_SELECTED = "selected";
    public static final String STATUS_SELECTED_MINOR_THRESHOLD = "selected_minor_threshold";
    //---------------------------------------


    public PredictedRna(){
        super(new Element(TAG_NAME));
    }
    public PredictedRna(Element elem) throws XMLElementException{
        super(elem);
        if(!elem.getName().equals(TAG_NAME)){
            throw new XMLElementException(XMLElementException.WRONG_TAG_NAME,new XMLElement(elem));
        }
    }
    public PredictedRna(String value) throws Exception{
        super(value);
        if(!root.getName().equals(TAG_NAME)){
            throw new XMLElementException(XMLElementException.WRONG_TAG_NAME,new XMLElement(value));
        }
    }

    public void addExtraStopCodon(Codon codon){
        initExtraStopCodonsTag();
        root.getChild(EXTRA_STOP_CODONS_TAG_NAME).addContent(codon.getRoot());
    }
    public void addFrameShift(Frameshift frameshift){
        initFrameshiftsTag();
        root.getChild(FRAME_SHIFTS_TAG_NAME).addContent(frameshift.getRoot());
    }

    //----------------SETTERS-------------------
    public void setId(String value){  setNodeText(ID_TAG_NAME, value);}
    public void setRnaName(String value){   setNodeText(RNA_NAME_TAG_NAME, value);}
    public void setSequence(String value){  setNodeText(SEQUENCE_TAG_NAME,value);}
    public void setHitDef(String value){ setNodeText(HIT_DEF_TAG_NAME, value);}
    public void setEvalue(double value){    setNodeText(EVALUE_TAG_NAME, String.valueOf(value));}
    public void setContigId(String value){  setNodeText(CONTIG_ID_TAG_NAME, value);}
    public void setStartPosition(int value){  setNodeText(START_POSITION_TAG_NAME, String.valueOf(value));}
    public void setStartIsCanonical(boolean value){ setNodeText(START_IS_CANONICAL_TAG_NAME,String.valueOf(value));}
    public void setEndPosition(int value){  setNodeText(END_POSITION_TAG_NAME, String.valueOf(value));}
    public void setEndIsCanonical(boolean value){   setNodeText(END_IS_CANONICAL_TAG_NAME, String.valueOf(value));}
    public void setStrand(String value){  setNodeText(STRAND_TAG_NAME, value);}
    public void setStrand(boolean value){
        if(value){
            setNodeText(STRAND_TAG_NAME, POSITIVE_STRAND);
        }else{
            setNodeText(STRAND_TAG_NAME, NEGATIVE_STRAND);
        }
    }
    public void setAnnotationUniprotId(String value){  setNodeText(ANNOTATION_UNIPROT_ID_TAG_NAME, value);}
    public void setAnnotationScoreEvalue(String value){  setNodeText(ANNOTATION_SCORE_EVALUE_TAG_NAME, value);}
    public void setBlastHitStart(int value){  setNodeText(BLAST_HIT_START_TAG_NAME, String.valueOf(value));}
    public void setBlastHitEnd(int value){  setNodeText(BLAST_HIT_END_TAG_NAME, String.valueOf(value));}
    public void setDnaSequence(String value){   setNodeText(DNA_SEQUENCE_TAG_NAME, value);}
    public void setStartCodon(Codon codon){
        initStartCodonTag();
        Element temp = root.getChild(START_CODON_TAG_NAME);
        temp.removeChildren(Codon.TAG_NAME);
        temp.addContent(codon.getRoot());
    }
    public void setStopCodon(Codon codon){
        initStopCodonTag();
        Element temp = root.getChild(STOP_CODON_TAG_NAME);
        temp.removeChildren(Codon.TAG_NAME);
        temp.addContent(codon.getRoot());
    }
    public void setHspSet(HspSet value){
        root.removeChildren(HspSet.TAG_NAME);
        root.addContent(value.toXML().getRoot());
    }

    //----------------GETTERS---------------------
    public String getId( ){  return getNodeText(ID_TAG_NAME);}
    public String getRnaName( ){  return getNodeText(RNA_NAME_TAG_NAME);}
    public String getHitDef(){   return getNodeText(HIT_DEF_TAG_NAME);}
    public String getSequence(){    return getNodeText(SEQUENCE_TAG_NAME);}
    public double getEvalue(){  return Double.parseDouble(getNodeText(EVALUE_TAG_NAME));}
    public String getContigId( ){  return getNodeText(CONTIG_ID_TAG_NAME);}
    public int getStartPosition( ){  return Integer.parseInt(getNodeText(START_POSITION_TAG_NAME));}
    public boolean getStartIsCanonical(){   return Boolean.parseBoolean(getNodeText(START_IS_CANONICAL_TAG_NAME));}
    public int getEndPosition( ){  return Integer.parseInt(getNodeText(END_POSITION_TAG_NAME));}
    public boolean getEndIsCanonical(){ return Boolean.parseBoolean(getNodeText(END_IS_CANONICAL_TAG_NAME));}
    public String getStrand( ){  return getNodeText(STRAND_TAG_NAME);}
    public String getAnnotationUniprotId( ){  return getNodeText(ANNOTATION_UNIPROT_ID_TAG_NAME);}
    public String getAnnotationScoreEvalue( ){  return getNodeText(ANNOTATION_SCORE_EVALUE_TAG_NAME);}
    public String getBlastHitStart( ){  return getNodeText(BLAST_HIT_START_TAG_NAME);}
    public String getBlastHitEnd( ){  return getNodeText(BLAST_HIT_END_TAG_NAME);}
    public String getDnaSequence(){ return getNodeText(DNA_SEQUENCE_TAG_NAME);}
    public HspSet getHspSet() throws XMLElementException{
        HspSet set = null;
        Element temp = root.getChild(HspSet.TAG_NAME);
        if(temp != null){
            set = new HspSet(temp);
        }
        return set;
    }
    public int getHspSetHitFrom() throws XMLElementException{   return getHspSet().getHspHitFrom();  }
    public int getHspSetHitTo() throws XMLElementException{    return getHspSet().getHspHitTo();}
    public Codon getInitCodon() throws XMLElementException{
        Codon temp = null;
        Element elem = root.getChild(START_CODON_TAG_NAME);
        if(elem != null){
            Element elem2 = elem.getChild(Codon.TAG_NAME);
            if(elem2 != null){
                temp = new Codon(elem2);
            }
        }
        return temp;
    }
    public Codon getStopCodon() throws XMLElementException{
        Codon temp = null;
        Element elem = root.getChild(STOP_CODON_TAG_NAME);
        if(elem != null){
            Element elem2 = elem.getChild(Codon.TAG_NAME);
            if(elem2 != null){
                temp = new Codon(elem2);
            }
        }
        return temp;
    }

    public ArrayList<Frameshift> getFrameshifts() throws XMLElementException{
        ArrayList<Frameshift> array = new ArrayList<>();
        Element temp = root.getChild(FRAME_SHIFTS_TAG_NAME);
        if(temp != null){
            List<Element> list = temp.getChildren(Frameshift.TAG_NAME);
            for(Element elem : list){
                Frameshift frameshift = new Frameshift(elem);
                array.add(frameshift);
            }
        }
        return array;
    }


    private void initStartCodonTag(){
        Element temp = root.getChild(START_CODON_TAG_NAME);
        if(temp == null){
            root.addContent(new Element(START_CODON_TAG_NAME));
        }
    }
    private void initStopCodonTag(){
        Element temp = root.getChild(STOP_CODON_TAG_NAME);
        if(temp == null){
            root.addContent(new Element(STOP_CODON_TAG_NAME));
        }
    }
    private void initExtraStopCodonsTag(){
        Element temp = root.getChild(EXTRA_STOP_CODONS_TAG_NAME);
        if(temp == null){
            root.addContent(new Element(EXTRA_STOP_CODONS_TAG_NAME));
        }
    }
    private void initFrameshiftsTag(){
        Element temp = root.getChild(FRAME_SHIFTS_TAG_NAME);
        if(temp == null){
            root.addContent(new Element(FRAME_SHIFTS_TAG_NAME));
        }
    }

    @Override
    public int compareTo(PredictedRna o) {

        int beginPos, endPos,beginOtherPos,endOtherPos;
        beginPos = this.getStartPosition();
        endPos = this.getEndPosition();
        if(this.getStrand().equals(PredictedRna.NEGATIVE_STRAND)){
            int swapPos = beginPos;
            beginPos = endPos;
            endPos = swapPos;
        }
        beginOtherPos = o.getStartPosition();
        endOtherPos = o.getEndPosition();
        if(o.getStrand().equals(PredictedRna.NEGATIVE_STRAND)){
            int swapPos = beginOtherPos;
            beginOtherPos = endOtherPos;
            endOtherPos = swapPos;
        }


        if(beginPos < beginOtherPos){
            return -1;
        }else if(beginPos > beginOtherPos){
            return 1;
        }else{
            if(endPos < endOtherPos){
                return -1;
            }else if(endPos > endOtherPos){
                return 1;
            }else{
                if(this.getEvalue() < o.getEvalue()){
                    return -1;
                }else if(this.getEvalue() > o.getEvalue()){
                    return 1;
                }else{
                    return 0;
                }
            }
        }
    }
}

```




[main/java/com/ohnosequences/BioinfoUtil.java]: ../../BioinfoUtil.java.md
[main/java/com/ohnosequences/util/BitOperations.java]: ../../util/BitOperations.java.md
[main/java/com/ohnosequences/util/blast/BlastExporter.java]: ../../util/blast/BlastExporter.java.md
[main/java/com/ohnosequences/util/blast/BlastSubset.java]: ../../util/blast/BlastSubset.java.md
[main/java/com/ohnosequences/util/CodonUtil.java]: ../../util/CodonUtil.java.md
[main/java/com/ohnosequences/util/Entry.java]: ../../util/Entry.java.md
[main/java/com/ohnosequences/util/Executable.java]: ../../util/Executable.java.md
[main/java/com/ohnosequences/util/ExecuteFromFile.java]: ../../util/ExecuteFromFile.java.md
[main/java/com/ohnosequences/util/fasta/FastaSubSeq.java]: ../../util/fasta/FastaSubSeq.java.md
[main/java/com/ohnosequences/util/fasta/FastaUtil.java]: ../../util/fasta/FastaUtil.java.md
[main/java/com/ohnosequences/util/fasta/MultifastaSelector.java]: ../../util/fasta/MultifastaSelector.java.md
[main/java/com/ohnosequences/util/fasta/SearchFastaHeaders.java]: ../../util/fasta/SearchFastaHeaders.java.md
[main/java/com/ohnosequences/util/fasta/SearchFastaSequence.java]: ../../util/fasta/SearchFastaSequence.java.md
[main/java/com/ohnosequences/util/file/FileUtil.java]: ../../util/file/FileUtil.java.md
[main/java/com/ohnosequences/util/file/FnaFileFilter.java]: ../../util/file/FnaFileFilter.java.md
[main/java/com/ohnosequences/util/file/GenomeFilesParser.java]: ../../util/file/GenomeFilesParser.java.md
[main/java/com/ohnosequences/util/file/PttFileFilter.java]: ../../util/file/PttFileFilter.java.md
[main/java/com/ohnosequences/util/file/RntFileFilter.java]: ../../util/file/RntFileFilter.java.md
[main/java/com/ohnosequences/util/genbank/GBCommon.java]: ../../util/genbank/GBCommon.java.md
[main/java/com/ohnosequences/util/gephi/GephiExporter.java]: ../../util/gephi/GephiExporter.java.md
[main/java/com/ohnosequences/util/gephi/GexfToDotExporter.java]: ../../util/gephi/GexfToDotExporter.java.md
[main/java/com/ohnosequences/util/go/GOExporter.java]: ../../util/go/GOExporter.java.md
[main/java/com/ohnosequences/util/model/Feature.java]: ../../util/model/Feature.java.md
[main/java/com/ohnosequences/util/model/Intergenic.java]: ../../util/model/Intergenic.java.md
[main/java/com/ohnosequences/util/model/PalindromicityResult.java]: ../../util/model/PalindromicityResult.java.md
[main/java/com/ohnosequences/util/ncbi/TaxonomyLoader.java]: ../../util/ncbi/TaxonomyLoader.java.md
[main/java/com/ohnosequences/util/oric/OricDataRetriever.java]: ../../util/oric/OricDataRetriever.java.md
[main/java/com/ohnosequences/util/Pair.java]: ../../util/Pair.java.md
[main/java/com/ohnosequences/util/pal/PalindromicityAnalyzer.java]: ../../util/pal/PalindromicityAnalyzer.java.md
[main/java/com/ohnosequences/util/security/MD5.java]: ../../util/security/MD5.java.md
[main/java/com/ohnosequences/util/seq/SeqUtil.java]: ../../util/seq/SeqUtil.java.md
[main/java/com/ohnosequences/util/statistics/StatisticalValues.java]: ../../util/statistics/StatisticalValues.java.md
[main/java/com/ohnosequences/util/uniprot/UniprotProteinRetreiver.java]: ../../util/uniprot/UniprotProteinRetreiver.java.md
[main/java/com/ohnosequences/xml/api/interfaces/IAttribute.java]: ../api/interfaces/IAttribute.java.md
[main/java/com/ohnosequences/xml/api/interfaces/IElement.java]: ../api/interfaces/IElement.java.md
[main/java/com/ohnosequences/xml/api/interfaces/INameSpace.java]: ../api/interfaces/INameSpace.java.md
[main/java/com/ohnosequences/xml/api/interfaces/IXmlThing.java]: ../api/interfaces/IXmlThing.java.md
[main/java/com/ohnosequences/xml/api/interfaces/package-info.java]: ../api/interfaces/package-info.java.md
[main/java/com/ohnosequences/xml/api/model/NameSpace.java]: ../api/model/NameSpace.java.md
[main/java/com/ohnosequences/xml/api/model/package-info.java]: ../api/model/package-info.java.md
[main/java/com/ohnosequences/xml/api/model/XMLAttribute.java]: ../api/model/XMLAttribute.java.md
[main/java/com/ohnosequences/xml/api/model/XMLElement.java]: ../api/model/XMLElement.java.md
[main/java/com/ohnosequences/xml/api/model/XMLElementException.java]: ../api/model/XMLElementException.java.md
[main/java/com/ohnosequences/xml/api/util/XMLUtil.java]: ../api/util/XMLUtil.java.md
[main/java/com/ohnosequences/xml/model/Annotation.java]: Annotation.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jNodeIndexXML.java]: bio4j/Bio4jNodeIndexXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jNodeXML.java]: bio4j/Bio4jNodeXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jPropertyXML.java]: bio4j/Bio4jPropertyXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jRelationshipIndexXML.java]: bio4j/Bio4jRelationshipIndexXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jRelationshipXML.java]: bio4j/Bio4jRelationshipXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/UniprotDataXML.java]: bio4j/UniprotDataXML.java.md
[main/java/com/ohnosequences/xml/model/BlastOutput.java]: BlastOutput.java.md
[main/java/com/ohnosequences/xml/model/BlastOutputParam.java]: BlastOutputParam.java.md
[main/java/com/ohnosequences/xml/model/Codon.java]: Codon.java.md
[main/java/com/ohnosequences/xml/model/ContigXML.java]: ContigXML.java.md
[main/java/com/ohnosequences/xml/model/cufflinks/CuffLinksElement.java]: cufflinks/CuffLinksElement.java.md
[main/java/com/ohnosequences/xml/model/embl/EmblXML.java]: embl/EmblXML.java.md
[main/java/com/ohnosequences/xml/model/Frameshift.java]: Frameshift.java.md
[main/java/com/ohnosequences/xml/model/Gap.java]: Gap.java.md
[main/java/com/ohnosequences/xml/model/gb/GenBankXML.java]: gb/GenBankXML.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/Feature.java]: genome/feature/Feature.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/Intergenic.java]: genome/feature/Intergenic.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/MisRNA.java]: genome/feature/MisRNA.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/ORF.java]: genome/feature/ORF.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/RNA.java]: genome/feature/RNA.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/RRNA.java]: genome/feature/RRNA.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/TRNA.java]: genome/feature/TRNA.java.md
[main/java/com/ohnosequences/xml/model/genome/GenomeElement.java]: genome/GenomeElement.java.md
[main/java/com/ohnosequences/xml/model/gexf/AttributesXML.java]: gexf/AttributesXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/AttributeXML.java]: gexf/AttributeXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/AttValuesXML.java]: gexf/AttValuesXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/AttValueXML.java]: gexf/AttValueXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/EdgesXML.java]: gexf/EdgesXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/EdgeXML.java]: gexf/EdgeXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/GexfXML.java]: gexf/GexfXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/GraphXML.java]: gexf/GraphXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/NodesXML.java]: gexf/NodesXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/NodeXML.java]: gexf/NodeXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/SpellsXML.java]: gexf/SpellsXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/SpellXML.java]: gexf/SpellXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/viz/VizColorXML.java]: gexf/viz/VizColorXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/viz/VizPositionXML.java]: gexf/viz/VizPositionXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/viz/VizSizeXML.java]: gexf/viz/VizSizeXML.java.md
[main/java/com/ohnosequences/xml/model/go/GoAnnotationXML.java]: go/GoAnnotationXML.java.md
[main/java/com/ohnosequences/xml/model/go/GOSlimXML.java]: go/GOSlimXML.java.md
[main/java/com/ohnosequences/xml/model/go/GoTermXML.java]: go/GoTermXML.java.md
[main/java/com/ohnosequences/xml/model/go/SlimSetXML.java]: go/SlimSetXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/DataXML.java]: graphml/DataXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/EdgeXML.java]: graphml/EdgeXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/GraphmlXML.java]: graphml/GraphmlXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/GraphXML.java]: graphml/GraphXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/KeyXML.java]: graphml/KeyXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/NodeXML.java]: graphml/NodeXML.java.md
[main/java/com/ohnosequences/xml/model/Hit.java]: Hit.java.md
[main/java/com/ohnosequences/xml/model/Hsp.java]: Hsp.java.md
[main/java/com/ohnosequences/xml/model/HspSet.java]: HspSet.java.md
[main/java/com/ohnosequences/xml/model/Iteration.java]: Iteration.java.md
[main/java/com/ohnosequences/xml/model/logs/LogRecordXML.java]: logs/LogRecordXML.java.md
[main/java/com/ohnosequences/xml/model/metagenomics/ReadResultXML.java]: metagenomics/ReadResultXML.java.md
[main/java/com/ohnosequences/xml/model/metagenomics/ReadXML.java]: metagenomics/ReadXML.java.md
[main/java/com/ohnosequences/xml/model/metagenomics/SampleXML.java]: metagenomics/SampleXML.java.md
[main/java/com/ohnosequences/xml/model/MetagenomicsDataXML.java]: MetagenomicsDataXML.java.md
[main/java/com/ohnosequences/xml/model/mg7/MG7DataXML.java]: mg7/MG7DataXML.java.md
[main/java/com/ohnosequences/xml/model/mg7/ReadResultXML.java]: mg7/ReadResultXML.java.md
[main/java/com/ohnosequences/xml/model/mg7/SampleXML.java]: mg7/SampleXML.java.md
[main/java/com/ohnosequences/xml/model/ncbi/NCBITaxonomyNodeXML.java]: ncbi/NCBITaxonomyNodeXML.java.md
[main/java/com/ohnosequences/xml/model/oric/Oric.java]: oric/Oric.java.md
[main/java/com/ohnosequences/xml/model/Overlap.java]: Overlap.java.md
[main/java/com/ohnosequences/xml/model/pal/PalindromicityResultXML.java]: pal/PalindromicityResultXML.java.md
[main/java/com/ohnosequences/xml/model/pg/Primer.java]: pg/Primer.java.md
[main/java/com/ohnosequences/xml/model/PredictedGene.java]: PredictedGene.java.md
[main/java/com/ohnosequences/xml/model/PredictedGenes.java]: PredictedGenes.java.md
[main/java/com/ohnosequences/xml/model/PredictedRna.java]: PredictedRna.java.md
[main/java/com/ohnosequences/xml/model/PredictedRnas.java]: PredictedRnas.java.md
[main/java/com/ohnosequences/xml/model/uniprot/ArticleXML.java]: uniprot/ArticleXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/CommentXML.java]: uniprot/CommentXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/FeatureXML.java]: uniprot/FeatureXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/InterproXML.java]: uniprot/InterproXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/IsoformXML.java]: uniprot/IsoformXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/KeywordXML.java]: uniprot/KeywordXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/ProteinXML.java]: uniprot/ProteinXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/SubcellularLocationXML.java]: uniprot/SubcellularLocationXML.java.md
[main/java/com/ohnosequences/xml/model/util/Argument.java]: util/Argument.java.md
[main/java/com/ohnosequences/xml/model/util/Arguments.java]: util/Arguments.java.md
[main/java/com/ohnosequences/xml/model/util/Error.java]: util/Error.java.md
[main/java/com/ohnosequences/xml/model/util/Execution.java]: util/Execution.java.md
[main/java/com/ohnosequences/xml/model/util/FlexXMLWrapperClassCreator.java]: util/FlexXMLWrapperClassCreator.java.md
[main/java/com/ohnosequences/xml/model/util/ScheduledExecutions.java]: util/ScheduledExecutions.java.md
[main/java/com/ohnosequences/xml/model/util/XMLWrapperClass.java]: util/XMLWrapperClass.java.md
[main/java/com/ohnosequences/xml/model/util/XMLWrapperClassCreator.java]: util/XMLWrapperClassCreator.java.md
[main/java/com/ohnosequences/xml/model/wip/Region.java]: wip/Region.java.md
[main/java/com/ohnosequences/xml/model/wip/WipPosition.java]: wip/WipPosition.java.md
[main/java/com/ohnosequences/xml/model/wip/WipResult.java]: wip/WipResult.java.md