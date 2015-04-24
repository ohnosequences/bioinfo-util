
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
package com.era7.bioinfoxml;

import com.era7.era7xmlapi.model.XMLElement;
import com.era7.era7xmlapi.model.XMLElementException;
import org.jdom2.Element;

/**
 *
 * @author ppareja
 */
public class Annotation extends XMLElement {

    public static final String TAG_NAME = "annotation";

    public Annotation() {
        super(new Element(TAG_NAME));
    }

    public Annotation(Element elem) throws XMLElementException {
        super(elem);
        if (!elem.getName().equals(TAG_NAME)) {
            throw new XMLElementException(XMLElementException.WRONG_TAG_NAME, new XMLElement(elem));
        }
    }

    public Annotation(String value) throws Exception {
        super(value);
        if (!root.getName().equals(TAG_NAME)) {
            throw new XMLElementException(XMLElementException.WRONG_TAG_NAME, new XMLElement(value));
        }
    }

    public void setPredictedGenes(PredictedGenes value) {
        root.removeChildren(PredictedGenes.TAG_NAME);
        root.addContent(value.asJDomElement());
    }

    public void setPredictedRnas(PredictedRnas value) {
        root.removeChildren(PredictedRnas.TAG_NAME);
        root.addContent(value.asJDomElement());
    }

    public PredictedGenes getPredictedGenes() throws XMLElementException {

        PredictedGenes pGenes = null;
        Element elem = root.getChild(PredictedGenes.TAG_NAME);
        if (elem != null) {
            pGenes = new PredictedGenes(elem);
        }

        return pGenes;
    }

    public PredictedRnas getPredictedRnas() throws XMLElementException {
        
        PredictedRnas pRnas = null;
        Element elem = root.getChild(PredictedRnas.TAG_NAME);
        if (elem != null) {
            pRnas = new PredictedRnas(elem);
        }

        return pRnas;
    }
}

```


------

### Index

+ src
  + test
    + java
    + scala
  + main
    + java
      + com
        + era7
          + era7xmlapi
            + util
              + [XMLUtil.java][main/java/com/era7/era7xmlapi/util/XMLUtil.java]
            + model
              + [NameSpace.java][main/java/com/era7/era7xmlapi/model/NameSpace.java]
              + [XMLElement.java][main/java/com/era7/era7xmlapi/model/XMLElement.java]
              + [XMLElementException.java][main/java/com/era7/era7xmlapi/model/XMLElementException.java]
              + [XMLAttribute.java][main/java/com/era7/era7xmlapi/model/XMLAttribute.java]
              + [package-info.java][main/java/com/era7/era7xmlapi/model/package-info.java]
            + interfaces
              + [IAttribute.java][main/java/com/era7/era7xmlapi/interfaces/IAttribute.java]
              + [IElement.java][main/java/com/era7/era7xmlapi/interfaces/IElement.java]
              + [IXmlThing.java][main/java/com/era7/era7xmlapi/interfaces/IXmlThing.java]
              + [INameSpace.java][main/java/com/era7/era7xmlapi/interfaces/INameSpace.java]
              + [package-info.java][main/java/com/era7/era7xmlapi/interfaces/package-info.java]
          + bioinfo
            + bioinfoaws
              + util
                + [AvailabilityZones.java][main/java/com/era7/bioinfo/bioinfoaws/util/AvailabilityZones.java]
                + [CredentialsRetriever.java][main/java/com/era7/bioinfo/bioinfoaws/util/CredentialsRetriever.java]
                + [Endpoints.java][main/java/com/era7/bioinfo/bioinfoaws/util/Endpoints.java]
                + [InstanceTypes.java][main/java/com/era7/bioinfo/bioinfoaws/util/InstanceTypes.java]
                + [AMITypes.java][main/java/com/era7/bioinfo/bioinfoaws/util/AMITypes.java]
              + s3
                + [S3FileUploader.java][main/java/com/era7/bioinfo/bioinfoaws/s3/S3FileUploader.java]
                + [S3FileDownloader.java][main/java/com/era7/bioinfo/bioinfoaws/s3/S3FileDownloader.java]
              + ec2
                + [SpotUtil.java][main/java/com/era7/bioinfo/bioinfoaws/ec2/SpotUtil.java]
                + [InstanceUtil.java][main/java/com/era7/bioinfo/bioinfoaws/ec2/InstanceUtil.java]
            + bioinfoneo4j
              + [Neo4jManager.java][main/java/com/era7/bioinfo/bioinfoneo4j/Neo4jManager.java]
              + [BasicRelationship.java][main/java/com/era7/bioinfo/bioinfoneo4j/BasicRelationship.java]
              + [BasicEntity.java][main/java/com/era7/bioinfo/bioinfoneo4j/BasicEntity.java]
            + bioinfoutil
              + fasta
                + [FastaUtil.java][main/java/com/era7/bioinfo/bioinfoutil/fasta/FastaUtil.java]
              + file
                + [GenomeFilesParser.java][main/java/com/era7/bioinfo/bioinfoutil/file/GenomeFilesParser.java]
                + [FnaFileFilter.java][main/java/com/era7/bioinfo/bioinfoutil/file/FnaFileFilter.java]
                + [RntFileFilter.java][main/java/com/era7/bioinfo/bioinfoutil/file/RntFileFilter.java]
                + [PttFileFilter.java][main/java/com/era7/bioinfo/bioinfoutil/file/PttFileFilter.java]
                + [FileUtil.java][main/java/com/era7/bioinfo/bioinfoutil/file/FileUtil.java]
              + statistics
                + [StatisticalValues.java][main/java/com/era7/bioinfo/bioinfoutil/statistics/StatisticalValues.java]
              + [Pair.java][main/java/com/era7/bioinfo/bioinfoutil/Pair.java]
              + pal
                + [PalindromicityAnalyzer.java][main/java/com/era7/bioinfo/bioinfoutil/pal/PalindromicityAnalyzer.java]
              + [Entry.java][main/java/com/era7/bioinfo/bioinfoutil/Entry.java]
              + go
                + [GOExporter.java][main/java/com/era7/bioinfo/bioinfoutil/go/GOExporter.java]
              + uniprot
                + [UniprotProteinRetreiver.java][main/java/com/era7/bioinfo/bioinfoutil/uniprot/UniprotProteinRetreiver.java]
              + oric
                + [OricDataRetriever.java][main/java/com/era7/bioinfo/bioinfoutil/oric/OricDataRetriever.java]
              + blast
                + [BlastSubset.java][main/java/com/era7/bioinfo/bioinfoutil/blast/BlastSubset.java]
                + [BlastExporter.java][main/java/com/era7/bioinfo/bioinfoutil/blast/BlastExporter.java]
              + model
                + [PalindromicityResult.java][main/java/com/era7/bioinfo/bioinfoutil/model/PalindromicityResult.java]
                + [Intergenic.java][main/java/com/era7/bioinfo/bioinfoutil/model/Intergenic.java]
                + [Feature.java][main/java/com/era7/bioinfo/bioinfoutil/model/Feature.java]
              + genbank
                + [GBCommon.java][main/java/com/era7/bioinfo/bioinfoutil/genbank/GBCommon.java]
              + [CodonUtil.java][main/java/com/era7/bioinfo/bioinfoutil/CodonUtil.java]
              + security
                + [MD5.java][main/java/com/era7/bioinfo/bioinfoutil/security/MD5.java]
              + [Executable.java][main/java/com/era7/bioinfo/bioinfoutil/Executable.java]
              + [ExecuteFromFile.java][main/java/com/era7/bioinfo/bioinfoutil/ExecuteFromFile.java]
              + seq
                + [SeqUtil.java][main/java/com/era7/bioinfo/bioinfoutil/seq/SeqUtil.java]
              + [BitOperations.java][main/java/com/era7/bioinfo/bioinfoutil/BitOperations.java]
              + ncbi
                + [TaxonomyLoader.java][main/java/com/era7/bioinfo/bioinfoutil/ncbi/TaxonomyLoader.java]
              + gephi
                + [GephiExporter.java][main/java/com/era7/bioinfo/bioinfoutil/gephi/GephiExporter.java]
                + [GexfToDotExpoerter.java][main/java/com/era7/bioinfo/bioinfoutil/gephi/GexfToDotExpoerter.java]
          + bioinfoxml
            + gexf
              + [GraphXML.java][main/java/com/era7/bioinfoxml/gexf/GraphXML.java]
              + viz
                + [VizSizeXML.java][main/java/com/era7/bioinfoxml/gexf/viz/VizSizeXML.java]
                + [VizPositionXML.java][main/java/com/era7/bioinfoxml/gexf/viz/VizPositionXML.java]
                + [VizColorXML.java][main/java/com/era7/bioinfoxml/gexf/viz/VizColorXML.java]
              + [GexfXML.java][main/java/com/era7/bioinfoxml/gexf/GexfXML.java]
              + [NodeXML.java][main/java/com/era7/bioinfoxml/gexf/NodeXML.java]
              + [SpellXML.java][main/java/com/era7/bioinfoxml/gexf/SpellXML.java]
              + [EdgeXML.java][main/java/com/era7/bioinfoxml/gexf/EdgeXML.java]
              + [NodesXML.java][main/java/com/era7/bioinfoxml/gexf/NodesXML.java]
              + [AttributeXML.java][main/java/com/era7/bioinfoxml/gexf/AttributeXML.java]
              + [AttValuesXML.java][main/java/com/era7/bioinfoxml/gexf/AttValuesXML.java]
              + [AttValueXML.java][main/java/com/era7/bioinfoxml/gexf/AttValueXML.java]
              + [EdgesXML.java][main/java/com/era7/bioinfoxml/gexf/EdgesXML.java]
              + [SpellsXML.java][main/java/com/era7/bioinfoxml/gexf/SpellsXML.java]
              + [AttributesXML.java][main/java/com/era7/bioinfoxml/gexf/AttributesXML.java]
            + pal
              + [PalindromicityResultXML.java][main/java/com/era7/bioinfoxml/pal/PalindromicityResultXML.java]
            + [Annotation.java][main/java/com/era7/bioinfoxml/Annotation.java]
            + [PredictedRna.java][main/java/com/era7/bioinfoxml/PredictedRna.java]
            + mg7
              + [MG7DataXML.java][main/java/com/era7/bioinfoxml/mg7/MG7DataXML.java]
              + [ReadResultXML.java][main/java/com/era7/bioinfoxml/mg7/ReadResultXML.java]
              + [SampleXML.java][main/java/com/era7/bioinfoxml/mg7/SampleXML.java]
            + [PredictedRnas.java][main/java/com/era7/bioinfoxml/PredictedRnas.java]
            + genome
              + feature
                + [MisRNA.java][main/java/com/era7/bioinfoxml/genome/feature/MisRNA.java]
                + [RRNA.java][main/java/com/era7/bioinfoxml/genome/feature/RRNA.java]
                + [Intergenic.java][main/java/com/era7/bioinfoxml/genome/feature/Intergenic.java]
                + [Feature.java][main/java/com/era7/bioinfoxml/genome/feature/Feature.java]
                + [ORF.java][main/java/com/era7/bioinfoxml/genome/feature/ORF.java]
                + [TRNA.java][main/java/com/era7/bioinfoxml/genome/feature/TRNA.java]
                + [RNA.java][main/java/com/era7/bioinfoxml/genome/feature/RNA.java]
              + [GenomeElement.java][main/java/com/era7/bioinfoxml/genome/GenomeElement.java]
            + wip
              + [WipPosition.java][main/java/com/era7/bioinfoxml/wip/WipPosition.java]
              + [WipResult.java][main/java/com/era7/bioinfoxml/wip/WipResult.java]
              + [Region.java][main/java/com/era7/bioinfoxml/wip/Region.java]
            + [Hsp.java][main/java/com/era7/bioinfoxml/Hsp.java]
            + [Gap.java][main/java/com/era7/bioinfoxml/Gap.java]
            + [MetagenomicsDataXML.java][main/java/com/era7/bioinfoxml/MetagenomicsDataXML.java]
            + gb
              + [GenBankXML.java][main/java/com/era7/bioinfoxml/gb/GenBankXML.java]
            + go
              + [GOSlimXML.java][main/java/com/era7/bioinfoxml/go/GOSlimXML.java]
              + [SlimSetXML.java][main/java/com/era7/bioinfoxml/go/SlimSetXML.java]
              + [GoTermXML.java][main/java/com/era7/bioinfoxml/go/GoTermXML.java]
              + [GoAnnotationXML.java][main/java/com/era7/bioinfoxml/go/GoAnnotationXML.java]
            + util
              + [XMLWrapperClassCreator.java][main/java/com/era7/bioinfoxml/util/XMLWrapperClassCreator.java]
              + [Execution.java][main/java/com/era7/bioinfoxml/util/Execution.java]
              + [Error.java][main/java/com/era7/bioinfoxml/util/Error.java]
              + [XMLWrapperClass.java][main/java/com/era7/bioinfoxml/util/XMLWrapperClass.java]
              + [FlexXMLWrapperClassCreator.java][main/java/com/era7/bioinfoxml/util/FlexXMLWrapperClassCreator.java]
              + [Arguments.java][main/java/com/era7/bioinfoxml/util/Arguments.java]
              + [ScheduledExecutions.java][main/java/com/era7/bioinfoxml/util/ScheduledExecutions.java]
              + [Argument.java][main/java/com/era7/bioinfoxml/util/Argument.java]
            + metagenomics
              + [ReadResultXML.java][main/java/com/era7/bioinfoxml/metagenomics/ReadResultXML.java]
              + [ReadXML.java][main/java/com/era7/bioinfoxml/metagenomics/ReadXML.java]
              + [SampleXML.java][main/java/com/era7/bioinfoxml/metagenomics/SampleXML.java]
            + uniprot
              + [ProteinXML.java][main/java/com/era7/bioinfoxml/uniprot/ProteinXML.java]
              + [ArticleXML.java][main/java/com/era7/bioinfoxml/uniprot/ArticleXML.java]
              + [FeatureXML.java][main/java/com/era7/bioinfoxml/uniprot/FeatureXML.java]
              + [IsoformXML.java][main/java/com/era7/bioinfoxml/uniprot/IsoformXML.java]
              + [SubcellularLocationXML.java][main/java/com/era7/bioinfoxml/uniprot/SubcellularLocationXML.java]
              + [InterproXML.java][main/java/com/era7/bioinfoxml/uniprot/InterproXML.java]
              + [CommentXML.java][main/java/com/era7/bioinfoxml/uniprot/CommentXML.java]
              + [KeywordXML.java][main/java/com/era7/bioinfoxml/uniprot/KeywordXML.java]
            + oric
              + [Oric.java][main/java/com/era7/bioinfoxml/oric/Oric.java]
            + [ContigXML.java][main/java/com/era7/bioinfoxml/ContigXML.java]
            + [BlastOutput.java][main/java/com/era7/bioinfoxml/BlastOutput.java]
            + pg
              + [Primer.java][main/java/com/era7/bioinfoxml/pg/Primer.java]
            + [Iteration.java][main/java/com/era7/bioinfoxml/Iteration.java]
            + cufflinks
              + [CuffLinksElement.java][main/java/com/era7/bioinfoxml/cufflinks/CuffLinksElement.java]
            + [PredictedGene.java][main/java/com/era7/bioinfoxml/PredictedGene.java]
            + logs
              + [LogRecordXML.java][main/java/com/era7/bioinfoxml/logs/LogRecordXML.java]
            + [Frameshift.java][main/java/com/era7/bioinfoxml/Frameshift.java]
            + embl
              + [EmblXML.java][main/java/com/era7/bioinfoxml/embl/EmblXML.java]
            + [Hit.java][main/java/com/era7/bioinfoxml/Hit.java]
            + [BlastOutputParam.java][main/java/com/era7/bioinfoxml/BlastOutputParam.java]
            + [Overlap.java][main/java/com/era7/bioinfoxml/Overlap.java]
            + [HspSet.java][main/java/com/era7/bioinfoxml/HspSet.java]
            + bio4j
              + [UniprotDataXML.java][main/java/com/era7/bioinfoxml/bio4j/UniprotDataXML.java]
              + [Bio4jPropertyXML.java][main/java/com/era7/bioinfoxml/bio4j/Bio4jPropertyXML.java]
              + [Bio4jRelationshipIndexXML.java][main/java/com/era7/bioinfoxml/bio4j/Bio4jRelationshipIndexXML.java]
              + [Bio4jNodeXML.java][main/java/com/era7/bioinfoxml/bio4j/Bio4jNodeXML.java]
              + [Bio4jNodeIndexXML.java][main/java/com/era7/bioinfoxml/bio4j/Bio4jNodeIndexXML.java]
              + [Bio4jRelationshipXML.java][main/java/com/era7/bioinfoxml/bio4j/Bio4jRelationshipXML.java]
            + [PredictedGenes.java][main/java/com/era7/bioinfoxml/PredictedGenes.java]
            + ncbi
              + [NCBITaxonomyNodeXML.java][main/java/com/era7/bioinfoxml/ncbi/NCBITaxonomyNodeXML.java]
            + graphml
              + [GraphmlXML.java][main/java/com/era7/bioinfoxml/graphml/GraphmlXML.java]
              + [GraphXML.java][main/java/com/era7/bioinfoxml/graphml/GraphXML.java]
              + [KeyXML.java][main/java/com/era7/bioinfoxml/graphml/KeyXML.java]
              + [NodeXML.java][main/java/com/era7/bioinfoxml/graphml/NodeXML.java]
              + [EdgeXML.java][main/java/com/era7/bioinfoxml/graphml/EdgeXML.java]
              + [DataXML.java][main/java/com/era7/bioinfoxml/graphml/DataXML.java]
            + [Codon.java][main/java/com/era7/bioinfoxml/Codon.java]
        + ohnosequences
          + xml
            + api
              + util
                + [XMLUtil.java][main/java/com/ohnosequences/xml/api/util/XMLUtil.java]
              + model
                + [NameSpace.java][main/java/com/ohnosequences/xml/api/model/NameSpace.java]
                + [XMLElement.java][main/java/com/ohnosequences/xml/api/model/XMLElement.java]
                + [XMLElementException.java][main/java/com/ohnosequences/xml/api/model/XMLElementException.java]
                + [XMLAttribute.java][main/java/com/ohnosequences/xml/api/model/XMLAttribute.java]
                + [package-info.java][main/java/com/ohnosequences/xml/api/model/package-info.java]
              + interfaces
                + [IAttribute.java][main/java/com/ohnosequences/xml/api/interfaces/IAttribute.java]
                + [IElement.java][main/java/com/ohnosequences/xml/api/interfaces/IElement.java]
                + [IXmlThing.java][main/java/com/ohnosequences/xml/api/interfaces/IXmlThing.java]
                + [INameSpace.java][main/java/com/ohnosequences/xml/api/interfaces/INameSpace.java]
                + [package-info.java][main/java/com/ohnosequences/xml/api/interfaces/package-info.java]
            + model
              + gexf
                + [GraphXML.java][main/java/com/ohnosequences/xml/model/gexf/GraphXML.java]
                + viz
                  + [VizSizeXML.java][main/java/com/ohnosequences/xml/model/gexf/viz/VizSizeXML.java]
                  + [VizPositionXML.java][main/java/com/ohnosequences/xml/model/gexf/viz/VizPositionXML.java]
                  + [VizColorXML.java][main/java/com/ohnosequences/xml/model/gexf/viz/VizColorXML.java]
                + [GexfXML.java][main/java/com/ohnosequences/xml/model/gexf/GexfXML.java]
                + [NodeXML.java][main/java/com/ohnosequences/xml/model/gexf/NodeXML.java]
                + [SpellXML.java][main/java/com/ohnosequences/xml/model/gexf/SpellXML.java]
                + [EdgeXML.java][main/java/com/ohnosequences/xml/model/gexf/EdgeXML.java]
                + [NodesXML.java][main/java/com/ohnosequences/xml/model/gexf/NodesXML.java]
                + [AttributeXML.java][main/java/com/ohnosequences/xml/model/gexf/AttributeXML.java]
                + [AttValuesXML.java][main/java/com/ohnosequences/xml/model/gexf/AttValuesXML.java]
                + [AttValueXML.java][main/java/com/ohnosequences/xml/model/gexf/AttValueXML.java]
                + [EdgesXML.java][main/java/com/ohnosequences/xml/model/gexf/EdgesXML.java]
                + [SpellsXML.java][main/java/com/ohnosequences/xml/model/gexf/SpellsXML.java]
                + [AttributesXML.java][main/java/com/ohnosequences/xml/model/gexf/AttributesXML.java]
              + pal
                + [PalindromicityResultXML.java][main/java/com/ohnosequences/xml/model/pal/PalindromicityResultXML.java]
              + [Annotation.java][main/java/com/ohnosequences/xml/model/Annotation.java]
              + [PredictedRna.java][main/java/com/ohnosequences/xml/model/PredictedRna.java]
              + mg7
                + [MG7DataXML.java][main/java/com/ohnosequences/xml/model/mg7/MG7DataXML.java]
                + [ReadResultXML.java][main/java/com/ohnosequences/xml/model/mg7/ReadResultXML.java]
                + [SampleXML.java][main/java/com/ohnosequences/xml/model/mg7/SampleXML.java]
              + [PredictedRnas.java][main/java/com/ohnosequences/xml/model/PredictedRnas.java]
              + genome
                + feature
                  + [MisRNA.java][main/java/com/ohnosequences/xml/model/genome/feature/MisRNA.java]
                  + [RRNA.java][main/java/com/ohnosequences/xml/model/genome/feature/RRNA.java]
                  + [Intergenic.java][main/java/com/ohnosequences/xml/model/genome/feature/Intergenic.java]
                  + [Feature.java][main/java/com/ohnosequences/xml/model/genome/feature/Feature.java]
                  + [ORF.java][main/java/com/ohnosequences/xml/model/genome/feature/ORF.java]
                  + [TRNA.java][main/java/com/ohnosequences/xml/model/genome/feature/TRNA.java]
                  + [RNA.java][main/java/com/ohnosequences/xml/model/genome/feature/RNA.java]
                + [GenomeElement.java][main/java/com/ohnosequences/xml/model/genome/GenomeElement.java]
              + wip
                + [WipPosition.java][main/java/com/ohnosequences/xml/model/wip/WipPosition.java]
                + [WipResult.java][main/java/com/ohnosequences/xml/model/wip/WipResult.java]
                + [Region.java][main/java/com/ohnosequences/xml/model/wip/Region.java]
              + [Hsp.java][main/java/com/ohnosequences/xml/model/Hsp.java]
              + [Gap.java][main/java/com/ohnosequences/xml/model/Gap.java]
              + [MetagenomicsDataXML.java][main/java/com/ohnosequences/xml/model/MetagenomicsDataXML.java]
              + gb
                + [GenBankXML.java][main/java/com/ohnosequences/xml/model/gb/GenBankXML.java]
              + go
                + [GOSlimXML.java][main/java/com/ohnosequences/xml/model/go/GOSlimXML.java]
                + [SlimSetXML.java][main/java/com/ohnosequences/xml/model/go/SlimSetXML.java]
                + [GoTermXML.java][main/java/com/ohnosequences/xml/model/go/GoTermXML.java]
                + [GoAnnotationXML.java][main/java/com/ohnosequences/xml/model/go/GoAnnotationXML.java]
              + util
                + [XMLWrapperClassCreator.java][main/java/com/ohnosequences/xml/model/util/XMLWrapperClassCreator.java]
                + [Execution.java][main/java/com/ohnosequences/xml/model/util/Execution.java]
                + [Error.java][main/java/com/ohnosequences/xml/model/util/Error.java]
                + [XMLWrapperClass.java][main/java/com/ohnosequences/xml/model/util/XMLWrapperClass.java]
                + [FlexXMLWrapperClassCreator.java][main/java/com/ohnosequences/xml/model/util/FlexXMLWrapperClassCreator.java]
                + [Arguments.java][main/java/com/ohnosequences/xml/model/util/Arguments.java]
                + [ScheduledExecutions.java][main/java/com/ohnosequences/xml/model/util/ScheduledExecutions.java]
                + [Argument.java][main/java/com/ohnosequences/xml/model/util/Argument.java]
              + metagenomics
                + [ReadResultXML.java][main/java/com/ohnosequences/xml/model/metagenomics/ReadResultXML.java]
                + [ReadXML.java][main/java/com/ohnosequences/xml/model/metagenomics/ReadXML.java]
                + [SampleXML.java][main/java/com/ohnosequences/xml/model/metagenomics/SampleXML.java]
              + uniprot
                + [ProteinXML.java][main/java/com/ohnosequences/xml/model/uniprot/ProteinXML.java]
                + [ArticleXML.java][main/java/com/ohnosequences/xml/model/uniprot/ArticleXML.java]
                + [FeatureXML.java][main/java/com/ohnosequences/xml/model/uniprot/FeatureXML.java]
                + [IsoformXML.java][main/java/com/ohnosequences/xml/model/uniprot/IsoformXML.java]
                + [SubcellularLocationXML.java][main/java/com/ohnosequences/xml/model/uniprot/SubcellularLocationXML.java]
                + [InterproXML.java][main/java/com/ohnosequences/xml/model/uniprot/InterproXML.java]
                + [CommentXML.java][main/java/com/ohnosequences/xml/model/uniprot/CommentXML.java]
                + [KeywordXML.java][main/java/com/ohnosequences/xml/model/uniprot/KeywordXML.java]
              + oric
                + [Oric.java][main/java/com/ohnosequences/xml/model/oric/Oric.java]
              + [ContigXML.java][main/java/com/ohnosequences/xml/model/ContigXML.java]
              + [BlastOutput.java][main/java/com/ohnosequences/xml/model/BlastOutput.java]
              + pg
                + [Primer.java][main/java/com/ohnosequences/xml/model/pg/Primer.java]
              + [Iteration.java][main/java/com/ohnosequences/xml/model/Iteration.java]
              + cufflinks
                + [CuffLinksElement.java][main/java/com/ohnosequences/xml/model/cufflinks/CuffLinksElement.java]
              + [PredictedGene.java][main/java/com/ohnosequences/xml/model/PredictedGene.java]
              + logs
                + [LogRecordXML.java][main/java/com/ohnosequences/xml/model/logs/LogRecordXML.java]
              + [Frameshift.java][main/java/com/ohnosequences/xml/model/Frameshift.java]
              + embl
                + [EmblXML.java][main/java/com/ohnosequences/xml/model/embl/EmblXML.java]
              + [Hit.java][main/java/com/ohnosequences/xml/model/Hit.java]
              + [BlastOutputParam.java][main/java/com/ohnosequences/xml/model/BlastOutputParam.java]
              + [Overlap.java][main/java/com/ohnosequences/xml/model/Overlap.java]
              + [HspSet.java][main/java/com/ohnosequences/xml/model/HspSet.java]
              + bio4j
                + [UniprotDataXML.java][main/java/com/ohnosequences/xml/model/bio4j/UniprotDataXML.java]
                + [Bio4jPropertyXML.java][main/java/com/ohnosequences/xml/model/bio4j/Bio4jPropertyXML.java]
                + [Bio4jRelationshipIndexXML.java][main/java/com/ohnosequences/xml/model/bio4j/Bio4jRelationshipIndexXML.java]
                + [Bio4jNodeXML.java][main/java/com/ohnosequences/xml/model/bio4j/Bio4jNodeXML.java]
                + [Bio4jNodeIndexXML.java][main/java/com/ohnosequences/xml/model/bio4j/Bio4jNodeIndexXML.java]
                + [Bio4jRelationshipXML.java][main/java/com/ohnosequences/xml/model/bio4j/Bio4jRelationshipXML.java]
              + [PredictedGenes.java][main/java/com/ohnosequences/xml/model/PredictedGenes.java]
              + ncbi
                + [NCBITaxonomyNodeXML.java][main/java/com/ohnosequences/xml/model/ncbi/NCBITaxonomyNodeXML.java]
              + graphml
                + [GraphmlXML.java][main/java/com/ohnosequences/xml/model/graphml/GraphmlXML.java]
                + [GraphXML.java][main/java/com/ohnosequences/xml/model/graphml/GraphXML.java]
                + [KeyXML.java][main/java/com/ohnosequences/xml/model/graphml/KeyXML.java]
                + [NodeXML.java][main/java/com/ohnosequences/xml/model/graphml/NodeXML.java]
                + [EdgeXML.java][main/java/com/ohnosequences/xml/model/graphml/EdgeXML.java]
                + [DataXML.java][main/java/com/ohnosequences/xml/model/graphml/DataXML.java]
              + [Codon.java][main/java/com/ohnosequences/xml/model/Codon.java]
          + util
            + fasta
              + [FastaUtil.java][main/java/com/ohnosequences/util/fasta/FastaUtil.java]
            + file
              + [GenomeFilesParser.java][main/java/com/ohnosequences/util/file/GenomeFilesParser.java]
              + [FnaFileFilter.java][main/java/com/ohnosequences/util/file/FnaFileFilter.java]
              + [RntFileFilter.java][main/java/com/ohnosequences/util/file/RntFileFilter.java]
              + [PttFileFilter.java][main/java/com/ohnosequences/util/file/PttFileFilter.java]
              + [FileUtil.java][main/java/com/ohnosequences/util/file/FileUtil.java]
            + statistics
              + [StatisticalValues.java][main/java/com/ohnosequences/util/statistics/StatisticalValues.java]
            + [Pair.java][main/java/com/ohnosequences/util/Pair.java]
            + pal
              + [PalindromicityAnalyzer.java][main/java/com/ohnosequences/util/pal/PalindromicityAnalyzer.java]
            + [Entry.java][main/java/com/ohnosequences/util/Entry.java]
            + go
              + [GOExporter.java][main/java/com/ohnosequences/util/go/GOExporter.java]
            + uniprot
              + [UniprotProteinRetreiver.java][main/java/com/ohnosequences/util/uniprot/UniprotProteinRetreiver.java]
            + oric
              + [OricDataRetriever.java][main/java/com/ohnosequences/util/oric/OricDataRetriever.java]
            + blast
              + [BlastSubset.java][main/java/com/ohnosequences/util/blast/BlastSubset.java]
              + [BlastExporter.java][main/java/com/ohnosequences/util/blast/BlastExporter.java]
            + model
              + [PalindromicityResult.java][main/java/com/ohnosequences/util/model/PalindromicityResult.java]
              + [Intergenic.java][main/java/com/ohnosequences/util/model/Intergenic.java]
              + [Feature.java][main/java/com/ohnosequences/util/model/Feature.java]
            + genbank
              + [GBCommon.java][main/java/com/ohnosequences/util/genbank/GBCommon.java]
            + [CodonUtil.java][main/java/com/ohnosequences/util/CodonUtil.java]
            + security
              + [MD5.java][main/java/com/ohnosequences/util/security/MD5.java]
            + [Executable.java][main/java/com/ohnosequences/util/Executable.java]
            + [ExecuteFromFile.java][main/java/com/ohnosequences/util/ExecuteFromFile.java]
            + seq
              + [SeqUtil.java][main/java/com/ohnosequences/util/seq/SeqUtil.java]
            + [BitOperations.java][main/java/com/ohnosequences/util/BitOperations.java]
            + ncbi
              + [TaxonomyLoader.java][main/java/com/ohnosequences/util/ncbi/TaxonomyLoader.java]
            + gephi
              + [GephiExporter.java][main/java/com/ohnosequences/util/gephi/GephiExporter.java]
              + [GexfToDotExporter.java][main/java/com/ohnosequences/util/gephi/GexfToDotExporter.java]
          + aws
            + util
              + [AvailabilityZones.java][main/java/com/ohnosequences/aws/util/AvailabilityZones.java]
              + [CredentialsRetriever.java][main/java/com/ohnosequences/aws/util/CredentialsRetriever.java]
              + [Endpoints.java][main/java/com/ohnosequences/aws/util/Endpoints.java]
              + [InstanceTypes.java][main/java/com/ohnosequences/aws/util/InstanceTypes.java]
              + [AMITypes.java][main/java/com/ohnosequences/aws/util/AMITypes.java]
            + s3
              + [S3FileUploader.java][main/java/com/ohnosequences/aws/s3/S3FileUploader.java]
              + [S3FileDownloader.java][main/java/com/ohnosequences/aws/s3/S3FileDownloader.java]
            + ec2
              + [SpotUtil.java][main/java/com/ohnosequences/aws/ec2/SpotUtil.java]
              + [InstanceUtil.java][main/java/com/ohnosequences/aws/ec2/InstanceUtil.java]
    + scala

[main/java/com/era7/era7xmlapi/util/XMLUtil.java]: ../era7xmlapi/util/XMLUtil.java.md
[main/java/com/era7/era7xmlapi/model/NameSpace.java]: ../era7xmlapi/model/NameSpace.java.md
[main/java/com/era7/era7xmlapi/model/XMLElement.java]: ../era7xmlapi/model/XMLElement.java.md
[main/java/com/era7/era7xmlapi/model/XMLElementException.java]: ../era7xmlapi/model/XMLElementException.java.md
[main/java/com/era7/era7xmlapi/model/XMLAttribute.java]: ../era7xmlapi/model/XMLAttribute.java.md
[main/java/com/era7/era7xmlapi/model/package-info.java]: ../era7xmlapi/model/package-info.java.md
[main/java/com/era7/era7xmlapi/interfaces/IAttribute.java]: ../era7xmlapi/interfaces/IAttribute.java.md
[main/java/com/era7/era7xmlapi/interfaces/IElement.java]: ../era7xmlapi/interfaces/IElement.java.md
[main/java/com/era7/era7xmlapi/interfaces/IXmlThing.java]: ../era7xmlapi/interfaces/IXmlThing.java.md
[main/java/com/era7/era7xmlapi/interfaces/INameSpace.java]: ../era7xmlapi/interfaces/INameSpace.java.md
[main/java/com/era7/era7xmlapi/interfaces/package-info.java]: ../era7xmlapi/interfaces/package-info.java.md
[main/java/com/era7/bioinfo/bioinfoaws/util/AvailabilityZones.java]: ../bioinfo/bioinfoaws/util/AvailabilityZones.java.md
[main/java/com/era7/bioinfo/bioinfoaws/util/CredentialsRetriever.java]: ../bioinfo/bioinfoaws/util/CredentialsRetriever.java.md
[main/java/com/era7/bioinfo/bioinfoaws/util/Endpoints.java]: ../bioinfo/bioinfoaws/util/Endpoints.java.md
[main/java/com/era7/bioinfo/bioinfoaws/util/InstanceTypes.java]: ../bioinfo/bioinfoaws/util/InstanceTypes.java.md
[main/java/com/era7/bioinfo/bioinfoaws/util/AMITypes.java]: ../bioinfo/bioinfoaws/util/AMITypes.java.md
[main/java/com/era7/bioinfo/bioinfoaws/s3/S3FileUploader.java]: ../bioinfo/bioinfoaws/s3/S3FileUploader.java.md
[main/java/com/era7/bioinfo/bioinfoaws/s3/S3FileDownloader.java]: ../bioinfo/bioinfoaws/s3/S3FileDownloader.java.md
[main/java/com/era7/bioinfo/bioinfoaws/ec2/SpotUtil.java]: ../bioinfo/bioinfoaws/ec2/SpotUtil.java.md
[main/java/com/era7/bioinfo/bioinfoaws/ec2/InstanceUtil.java]: ../bioinfo/bioinfoaws/ec2/InstanceUtil.java.md
[main/java/com/era7/bioinfo/bioinfoneo4j/Neo4jManager.java]: ../bioinfo/bioinfoneo4j/Neo4jManager.java.md
[main/java/com/era7/bioinfo/bioinfoneo4j/BasicRelationship.java]: ../bioinfo/bioinfoneo4j/BasicRelationship.java.md
[main/java/com/era7/bioinfo/bioinfoneo4j/BasicEntity.java]: ../bioinfo/bioinfoneo4j/BasicEntity.java.md
[main/java/com/era7/bioinfo/bioinfoutil/fasta/FastaUtil.java]: ../bioinfo/bioinfoutil/fasta/FastaUtil.java.md
[main/java/com/era7/bioinfo/bioinfoutil/file/GenomeFilesParser.java]: ../bioinfo/bioinfoutil/file/GenomeFilesParser.java.md
[main/java/com/era7/bioinfo/bioinfoutil/file/FnaFileFilter.java]: ../bioinfo/bioinfoutil/file/FnaFileFilter.java.md
[main/java/com/era7/bioinfo/bioinfoutil/file/RntFileFilter.java]: ../bioinfo/bioinfoutil/file/RntFileFilter.java.md
[main/java/com/era7/bioinfo/bioinfoutil/file/PttFileFilter.java]: ../bioinfo/bioinfoutil/file/PttFileFilter.java.md
[main/java/com/era7/bioinfo/bioinfoutil/file/FileUtil.java]: ../bioinfo/bioinfoutil/file/FileUtil.java.md
[main/java/com/era7/bioinfo/bioinfoutil/statistics/StatisticalValues.java]: ../bioinfo/bioinfoutil/statistics/StatisticalValues.java.md
[main/java/com/era7/bioinfo/bioinfoutil/Pair.java]: ../bioinfo/bioinfoutil/Pair.java.md
[main/java/com/era7/bioinfo/bioinfoutil/pal/PalindromicityAnalyzer.java]: ../bioinfo/bioinfoutil/pal/PalindromicityAnalyzer.java.md
[main/java/com/era7/bioinfo/bioinfoutil/Entry.java]: ../bioinfo/bioinfoutil/Entry.java.md
[main/java/com/era7/bioinfo/bioinfoutil/go/GOExporter.java]: ../bioinfo/bioinfoutil/go/GOExporter.java.md
[main/java/com/era7/bioinfo/bioinfoutil/uniprot/UniprotProteinRetreiver.java]: ../bioinfo/bioinfoutil/uniprot/UniprotProteinRetreiver.java.md
[main/java/com/era7/bioinfo/bioinfoutil/oric/OricDataRetriever.java]: ../bioinfo/bioinfoutil/oric/OricDataRetriever.java.md
[main/java/com/era7/bioinfo/bioinfoutil/blast/BlastSubset.java]: ../bioinfo/bioinfoutil/blast/BlastSubset.java.md
[main/java/com/era7/bioinfo/bioinfoutil/blast/BlastExporter.java]: ../bioinfo/bioinfoutil/blast/BlastExporter.java.md
[main/java/com/era7/bioinfo/bioinfoutil/model/PalindromicityResult.java]: ../bioinfo/bioinfoutil/model/PalindromicityResult.java.md
[main/java/com/era7/bioinfo/bioinfoutil/model/Intergenic.java]: ../bioinfo/bioinfoutil/model/Intergenic.java.md
[main/java/com/era7/bioinfo/bioinfoutil/model/Feature.java]: ../bioinfo/bioinfoutil/model/Feature.java.md
[main/java/com/era7/bioinfo/bioinfoutil/genbank/GBCommon.java]: ../bioinfo/bioinfoutil/genbank/GBCommon.java.md
[main/java/com/era7/bioinfo/bioinfoutil/CodonUtil.java]: ../bioinfo/bioinfoutil/CodonUtil.java.md
[main/java/com/era7/bioinfo/bioinfoutil/security/MD5.java]: ../bioinfo/bioinfoutil/security/MD5.java.md
[main/java/com/era7/bioinfo/bioinfoutil/Executable.java]: ../bioinfo/bioinfoutil/Executable.java.md
[main/java/com/era7/bioinfo/bioinfoutil/ExecuteFromFile.java]: ../bioinfo/bioinfoutil/ExecuteFromFile.java.md
[main/java/com/era7/bioinfo/bioinfoutil/seq/SeqUtil.java]: ../bioinfo/bioinfoutil/seq/SeqUtil.java.md
[main/java/com/era7/bioinfo/bioinfoutil/BitOperations.java]: ../bioinfo/bioinfoutil/BitOperations.java.md
[main/java/com/era7/bioinfo/bioinfoutil/ncbi/TaxonomyLoader.java]: ../bioinfo/bioinfoutil/ncbi/TaxonomyLoader.java.md
[main/java/com/era7/bioinfo/bioinfoutil/gephi/GephiExporter.java]: ../bioinfo/bioinfoutil/gephi/GephiExporter.java.md
[main/java/com/era7/bioinfo/bioinfoutil/gephi/GexfToDotExpoerter.java]: ../bioinfo/bioinfoutil/gephi/GexfToDotExpoerter.java.md
[main/java/com/era7/bioinfoxml/gexf/GraphXML.java]: gexf/GraphXML.java.md
[main/java/com/era7/bioinfoxml/gexf/viz/VizSizeXML.java]: gexf/viz/VizSizeXML.java.md
[main/java/com/era7/bioinfoxml/gexf/viz/VizPositionXML.java]: gexf/viz/VizPositionXML.java.md
[main/java/com/era7/bioinfoxml/gexf/viz/VizColorXML.java]: gexf/viz/VizColorXML.java.md
[main/java/com/era7/bioinfoxml/gexf/GexfXML.java]: gexf/GexfXML.java.md
[main/java/com/era7/bioinfoxml/gexf/NodeXML.java]: gexf/NodeXML.java.md
[main/java/com/era7/bioinfoxml/gexf/SpellXML.java]: gexf/SpellXML.java.md
[main/java/com/era7/bioinfoxml/gexf/EdgeXML.java]: gexf/EdgeXML.java.md
[main/java/com/era7/bioinfoxml/gexf/NodesXML.java]: gexf/NodesXML.java.md
[main/java/com/era7/bioinfoxml/gexf/AttributeXML.java]: gexf/AttributeXML.java.md
[main/java/com/era7/bioinfoxml/gexf/AttValuesXML.java]: gexf/AttValuesXML.java.md
[main/java/com/era7/bioinfoxml/gexf/AttValueXML.java]: gexf/AttValueXML.java.md
[main/java/com/era7/bioinfoxml/gexf/EdgesXML.java]: gexf/EdgesXML.java.md
[main/java/com/era7/bioinfoxml/gexf/SpellsXML.java]: gexf/SpellsXML.java.md
[main/java/com/era7/bioinfoxml/gexf/AttributesXML.java]: gexf/AttributesXML.java.md
[main/java/com/era7/bioinfoxml/pal/PalindromicityResultXML.java]: pal/PalindromicityResultXML.java.md
[main/java/com/era7/bioinfoxml/Annotation.java]: Annotation.java.md
[main/java/com/era7/bioinfoxml/PredictedRna.java]: PredictedRna.java.md
[main/java/com/era7/bioinfoxml/mg7/MG7DataXML.java]: mg7/MG7DataXML.java.md
[main/java/com/era7/bioinfoxml/mg7/ReadResultXML.java]: mg7/ReadResultXML.java.md
[main/java/com/era7/bioinfoxml/mg7/SampleXML.java]: mg7/SampleXML.java.md
[main/java/com/era7/bioinfoxml/PredictedRnas.java]: PredictedRnas.java.md
[main/java/com/era7/bioinfoxml/genome/feature/MisRNA.java]: genome/feature/MisRNA.java.md
[main/java/com/era7/bioinfoxml/genome/feature/RRNA.java]: genome/feature/RRNA.java.md
[main/java/com/era7/bioinfoxml/genome/feature/Intergenic.java]: genome/feature/Intergenic.java.md
[main/java/com/era7/bioinfoxml/genome/feature/Feature.java]: genome/feature/Feature.java.md
[main/java/com/era7/bioinfoxml/genome/feature/ORF.java]: genome/feature/ORF.java.md
[main/java/com/era7/bioinfoxml/genome/feature/TRNA.java]: genome/feature/TRNA.java.md
[main/java/com/era7/bioinfoxml/genome/feature/RNA.java]: genome/feature/RNA.java.md
[main/java/com/era7/bioinfoxml/genome/GenomeElement.java]: genome/GenomeElement.java.md
[main/java/com/era7/bioinfoxml/wip/WipPosition.java]: wip/WipPosition.java.md
[main/java/com/era7/bioinfoxml/wip/WipResult.java]: wip/WipResult.java.md
[main/java/com/era7/bioinfoxml/wip/Region.java]: wip/Region.java.md
[main/java/com/era7/bioinfoxml/Hsp.java]: Hsp.java.md
[main/java/com/era7/bioinfoxml/Gap.java]: Gap.java.md
[main/java/com/era7/bioinfoxml/MetagenomicsDataXML.java]: MetagenomicsDataXML.java.md
[main/java/com/era7/bioinfoxml/gb/GenBankXML.java]: gb/GenBankXML.java.md
[main/java/com/era7/bioinfoxml/go/GOSlimXML.java]: go/GOSlimXML.java.md
[main/java/com/era7/bioinfoxml/go/SlimSetXML.java]: go/SlimSetXML.java.md
[main/java/com/era7/bioinfoxml/go/GoTermXML.java]: go/GoTermXML.java.md
[main/java/com/era7/bioinfoxml/go/GoAnnotationXML.java]: go/GoAnnotationXML.java.md
[main/java/com/era7/bioinfoxml/util/XMLWrapperClassCreator.java]: util/XMLWrapperClassCreator.java.md
[main/java/com/era7/bioinfoxml/util/Execution.java]: util/Execution.java.md
[main/java/com/era7/bioinfoxml/util/Error.java]: util/Error.java.md
[main/java/com/era7/bioinfoxml/util/XMLWrapperClass.java]: util/XMLWrapperClass.java.md
[main/java/com/era7/bioinfoxml/util/FlexXMLWrapperClassCreator.java]: util/FlexXMLWrapperClassCreator.java.md
[main/java/com/era7/bioinfoxml/util/Arguments.java]: util/Arguments.java.md
[main/java/com/era7/bioinfoxml/util/ScheduledExecutions.java]: util/ScheduledExecutions.java.md
[main/java/com/era7/bioinfoxml/util/Argument.java]: util/Argument.java.md
[main/java/com/era7/bioinfoxml/metagenomics/ReadResultXML.java]: metagenomics/ReadResultXML.java.md
[main/java/com/era7/bioinfoxml/metagenomics/ReadXML.java]: metagenomics/ReadXML.java.md
[main/java/com/era7/bioinfoxml/metagenomics/SampleXML.java]: metagenomics/SampleXML.java.md
[main/java/com/era7/bioinfoxml/uniprot/ProteinXML.java]: uniprot/ProteinXML.java.md
[main/java/com/era7/bioinfoxml/uniprot/ArticleXML.java]: uniprot/ArticleXML.java.md
[main/java/com/era7/bioinfoxml/uniprot/FeatureXML.java]: uniprot/FeatureXML.java.md
[main/java/com/era7/bioinfoxml/uniprot/IsoformXML.java]: uniprot/IsoformXML.java.md
[main/java/com/era7/bioinfoxml/uniprot/SubcellularLocationXML.java]: uniprot/SubcellularLocationXML.java.md
[main/java/com/era7/bioinfoxml/uniprot/InterproXML.java]: uniprot/InterproXML.java.md
[main/java/com/era7/bioinfoxml/uniprot/CommentXML.java]: uniprot/CommentXML.java.md
[main/java/com/era7/bioinfoxml/uniprot/KeywordXML.java]: uniprot/KeywordXML.java.md
[main/java/com/era7/bioinfoxml/oric/Oric.java]: oric/Oric.java.md
[main/java/com/era7/bioinfoxml/ContigXML.java]: ContigXML.java.md
[main/java/com/era7/bioinfoxml/BlastOutput.java]: BlastOutput.java.md
[main/java/com/era7/bioinfoxml/pg/Primer.java]: pg/Primer.java.md
[main/java/com/era7/bioinfoxml/Iteration.java]: Iteration.java.md
[main/java/com/era7/bioinfoxml/cufflinks/CuffLinksElement.java]: cufflinks/CuffLinksElement.java.md
[main/java/com/era7/bioinfoxml/PredictedGene.java]: PredictedGene.java.md
[main/java/com/era7/bioinfoxml/logs/LogRecordXML.java]: logs/LogRecordXML.java.md
[main/java/com/era7/bioinfoxml/Frameshift.java]: Frameshift.java.md
[main/java/com/era7/bioinfoxml/embl/EmblXML.java]: embl/EmblXML.java.md
[main/java/com/era7/bioinfoxml/Hit.java]: Hit.java.md
[main/java/com/era7/bioinfoxml/BlastOutputParam.java]: BlastOutputParam.java.md
[main/java/com/era7/bioinfoxml/Overlap.java]: Overlap.java.md
[main/java/com/era7/bioinfoxml/HspSet.java]: HspSet.java.md
[main/java/com/era7/bioinfoxml/bio4j/UniprotDataXML.java]: bio4j/UniprotDataXML.java.md
[main/java/com/era7/bioinfoxml/bio4j/Bio4jPropertyXML.java]: bio4j/Bio4jPropertyXML.java.md
[main/java/com/era7/bioinfoxml/bio4j/Bio4jRelationshipIndexXML.java]: bio4j/Bio4jRelationshipIndexXML.java.md
[main/java/com/era7/bioinfoxml/bio4j/Bio4jNodeXML.java]: bio4j/Bio4jNodeXML.java.md
[main/java/com/era7/bioinfoxml/bio4j/Bio4jNodeIndexXML.java]: bio4j/Bio4jNodeIndexXML.java.md
[main/java/com/era7/bioinfoxml/bio4j/Bio4jRelationshipXML.java]: bio4j/Bio4jRelationshipXML.java.md
[main/java/com/era7/bioinfoxml/PredictedGenes.java]: PredictedGenes.java.md
[main/java/com/era7/bioinfoxml/ncbi/NCBITaxonomyNodeXML.java]: ncbi/NCBITaxonomyNodeXML.java.md
[main/java/com/era7/bioinfoxml/graphml/GraphmlXML.java]: graphml/GraphmlXML.java.md
[main/java/com/era7/bioinfoxml/graphml/GraphXML.java]: graphml/GraphXML.java.md
[main/java/com/era7/bioinfoxml/graphml/KeyXML.java]: graphml/KeyXML.java.md
[main/java/com/era7/bioinfoxml/graphml/NodeXML.java]: graphml/NodeXML.java.md
[main/java/com/era7/bioinfoxml/graphml/EdgeXML.java]: graphml/EdgeXML.java.md
[main/java/com/era7/bioinfoxml/graphml/DataXML.java]: graphml/DataXML.java.md
[main/java/com/era7/bioinfoxml/Codon.java]: Codon.java.md
[main/java/com/ohnosequences/xml/api/util/XMLUtil.java]: ../../ohnosequences/xml/api/util/XMLUtil.java.md
[main/java/com/ohnosequences/xml/api/model/NameSpace.java]: ../../ohnosequences/xml/api/model/NameSpace.java.md
[main/java/com/ohnosequences/xml/api/model/XMLElement.java]: ../../ohnosequences/xml/api/model/XMLElement.java.md
[main/java/com/ohnosequences/xml/api/model/XMLElementException.java]: ../../ohnosequences/xml/api/model/XMLElementException.java.md
[main/java/com/ohnosequences/xml/api/model/XMLAttribute.java]: ../../ohnosequences/xml/api/model/XMLAttribute.java.md
[main/java/com/ohnosequences/xml/api/model/package-info.java]: ../../ohnosequences/xml/api/model/package-info.java.md
[main/java/com/ohnosequences/xml/api/interfaces/IAttribute.java]: ../../ohnosequences/xml/api/interfaces/IAttribute.java.md
[main/java/com/ohnosequences/xml/api/interfaces/IElement.java]: ../../ohnosequences/xml/api/interfaces/IElement.java.md
[main/java/com/ohnosequences/xml/api/interfaces/IXmlThing.java]: ../../ohnosequences/xml/api/interfaces/IXmlThing.java.md
[main/java/com/ohnosequences/xml/api/interfaces/INameSpace.java]: ../../ohnosequences/xml/api/interfaces/INameSpace.java.md
[main/java/com/ohnosequences/xml/api/interfaces/package-info.java]: ../../ohnosequences/xml/api/interfaces/package-info.java.md
[main/java/com/ohnosequences/xml/model/gexf/GraphXML.java]: ../../ohnosequences/xml/model/gexf/GraphXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/viz/VizSizeXML.java]: ../../ohnosequences/xml/model/gexf/viz/VizSizeXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/viz/VizPositionXML.java]: ../../ohnosequences/xml/model/gexf/viz/VizPositionXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/viz/VizColorXML.java]: ../../ohnosequences/xml/model/gexf/viz/VizColorXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/GexfXML.java]: ../../ohnosequences/xml/model/gexf/GexfXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/NodeXML.java]: ../../ohnosequences/xml/model/gexf/NodeXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/SpellXML.java]: ../../ohnosequences/xml/model/gexf/SpellXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/EdgeXML.java]: ../../ohnosequences/xml/model/gexf/EdgeXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/NodesXML.java]: ../../ohnosequences/xml/model/gexf/NodesXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/AttributeXML.java]: ../../ohnosequences/xml/model/gexf/AttributeXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/AttValuesXML.java]: ../../ohnosequences/xml/model/gexf/AttValuesXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/AttValueXML.java]: ../../ohnosequences/xml/model/gexf/AttValueXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/EdgesXML.java]: ../../ohnosequences/xml/model/gexf/EdgesXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/SpellsXML.java]: ../../ohnosequences/xml/model/gexf/SpellsXML.java.md
[main/java/com/ohnosequences/xml/model/gexf/AttributesXML.java]: ../../ohnosequences/xml/model/gexf/AttributesXML.java.md
[main/java/com/ohnosequences/xml/model/pal/PalindromicityResultXML.java]: ../../ohnosequences/xml/model/pal/PalindromicityResultXML.java.md
[main/java/com/ohnosequences/xml/model/Annotation.java]: ../../ohnosequences/xml/model/Annotation.java.md
[main/java/com/ohnosequences/xml/model/PredictedRna.java]: ../../ohnosequences/xml/model/PredictedRna.java.md
[main/java/com/ohnosequences/xml/model/mg7/MG7DataXML.java]: ../../ohnosequences/xml/model/mg7/MG7DataXML.java.md
[main/java/com/ohnosequences/xml/model/mg7/ReadResultXML.java]: ../../ohnosequences/xml/model/mg7/ReadResultXML.java.md
[main/java/com/ohnosequences/xml/model/mg7/SampleXML.java]: ../../ohnosequences/xml/model/mg7/SampleXML.java.md
[main/java/com/ohnosequences/xml/model/PredictedRnas.java]: ../../ohnosequences/xml/model/PredictedRnas.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/MisRNA.java]: ../../ohnosequences/xml/model/genome/feature/MisRNA.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/RRNA.java]: ../../ohnosequences/xml/model/genome/feature/RRNA.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/Intergenic.java]: ../../ohnosequences/xml/model/genome/feature/Intergenic.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/Feature.java]: ../../ohnosequences/xml/model/genome/feature/Feature.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/ORF.java]: ../../ohnosequences/xml/model/genome/feature/ORF.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/TRNA.java]: ../../ohnosequences/xml/model/genome/feature/TRNA.java.md
[main/java/com/ohnosequences/xml/model/genome/feature/RNA.java]: ../../ohnosequences/xml/model/genome/feature/RNA.java.md
[main/java/com/ohnosequences/xml/model/genome/GenomeElement.java]: ../../ohnosequences/xml/model/genome/GenomeElement.java.md
[main/java/com/ohnosequences/xml/model/wip/WipPosition.java]: ../../ohnosequences/xml/model/wip/WipPosition.java.md
[main/java/com/ohnosequences/xml/model/wip/WipResult.java]: ../../ohnosequences/xml/model/wip/WipResult.java.md
[main/java/com/ohnosequences/xml/model/wip/Region.java]: ../../ohnosequences/xml/model/wip/Region.java.md
[main/java/com/ohnosequences/xml/model/Hsp.java]: ../../ohnosequences/xml/model/Hsp.java.md
[main/java/com/ohnosequences/xml/model/Gap.java]: ../../ohnosequences/xml/model/Gap.java.md
[main/java/com/ohnosequences/xml/model/MetagenomicsDataXML.java]: ../../ohnosequences/xml/model/MetagenomicsDataXML.java.md
[main/java/com/ohnosequences/xml/model/gb/GenBankXML.java]: ../../ohnosequences/xml/model/gb/GenBankXML.java.md
[main/java/com/ohnosequences/xml/model/go/GOSlimXML.java]: ../../ohnosequences/xml/model/go/GOSlimXML.java.md
[main/java/com/ohnosequences/xml/model/go/SlimSetXML.java]: ../../ohnosequences/xml/model/go/SlimSetXML.java.md
[main/java/com/ohnosequences/xml/model/go/GoTermXML.java]: ../../ohnosequences/xml/model/go/GoTermXML.java.md
[main/java/com/ohnosequences/xml/model/go/GoAnnotationXML.java]: ../../ohnosequences/xml/model/go/GoAnnotationXML.java.md
[main/java/com/ohnosequences/xml/model/util/XMLWrapperClassCreator.java]: ../../ohnosequences/xml/model/util/XMLWrapperClassCreator.java.md
[main/java/com/ohnosequences/xml/model/util/Execution.java]: ../../ohnosequences/xml/model/util/Execution.java.md
[main/java/com/ohnosequences/xml/model/util/Error.java]: ../../ohnosequences/xml/model/util/Error.java.md
[main/java/com/ohnosequences/xml/model/util/XMLWrapperClass.java]: ../../ohnosequences/xml/model/util/XMLWrapperClass.java.md
[main/java/com/ohnosequences/xml/model/util/FlexXMLWrapperClassCreator.java]: ../../ohnosequences/xml/model/util/FlexXMLWrapperClassCreator.java.md
[main/java/com/ohnosequences/xml/model/util/Arguments.java]: ../../ohnosequences/xml/model/util/Arguments.java.md
[main/java/com/ohnosequences/xml/model/util/ScheduledExecutions.java]: ../../ohnosequences/xml/model/util/ScheduledExecutions.java.md
[main/java/com/ohnosequences/xml/model/util/Argument.java]: ../../ohnosequences/xml/model/util/Argument.java.md
[main/java/com/ohnosequences/xml/model/metagenomics/ReadResultXML.java]: ../../ohnosequences/xml/model/metagenomics/ReadResultXML.java.md
[main/java/com/ohnosequences/xml/model/metagenomics/ReadXML.java]: ../../ohnosequences/xml/model/metagenomics/ReadXML.java.md
[main/java/com/ohnosequences/xml/model/metagenomics/SampleXML.java]: ../../ohnosequences/xml/model/metagenomics/SampleXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/ProteinXML.java]: ../../ohnosequences/xml/model/uniprot/ProteinXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/ArticleXML.java]: ../../ohnosequences/xml/model/uniprot/ArticleXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/FeatureXML.java]: ../../ohnosequences/xml/model/uniprot/FeatureXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/IsoformXML.java]: ../../ohnosequences/xml/model/uniprot/IsoformXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/SubcellularLocationXML.java]: ../../ohnosequences/xml/model/uniprot/SubcellularLocationXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/InterproXML.java]: ../../ohnosequences/xml/model/uniprot/InterproXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/CommentXML.java]: ../../ohnosequences/xml/model/uniprot/CommentXML.java.md
[main/java/com/ohnosequences/xml/model/uniprot/KeywordXML.java]: ../../ohnosequences/xml/model/uniprot/KeywordXML.java.md
[main/java/com/ohnosequences/xml/model/oric/Oric.java]: ../../ohnosequences/xml/model/oric/Oric.java.md
[main/java/com/ohnosequences/xml/model/ContigXML.java]: ../../ohnosequences/xml/model/ContigXML.java.md
[main/java/com/ohnosequences/xml/model/BlastOutput.java]: ../../ohnosequences/xml/model/BlastOutput.java.md
[main/java/com/ohnosequences/xml/model/pg/Primer.java]: ../../ohnosequences/xml/model/pg/Primer.java.md
[main/java/com/ohnosequences/xml/model/Iteration.java]: ../../ohnosequences/xml/model/Iteration.java.md
[main/java/com/ohnosequences/xml/model/cufflinks/CuffLinksElement.java]: ../../ohnosequences/xml/model/cufflinks/CuffLinksElement.java.md
[main/java/com/ohnosequences/xml/model/PredictedGene.java]: ../../ohnosequences/xml/model/PredictedGene.java.md
[main/java/com/ohnosequences/xml/model/logs/LogRecordXML.java]: ../../ohnosequences/xml/model/logs/LogRecordXML.java.md
[main/java/com/ohnosequences/xml/model/Frameshift.java]: ../../ohnosequences/xml/model/Frameshift.java.md
[main/java/com/ohnosequences/xml/model/embl/EmblXML.java]: ../../ohnosequences/xml/model/embl/EmblXML.java.md
[main/java/com/ohnosequences/xml/model/Hit.java]: ../../ohnosequences/xml/model/Hit.java.md
[main/java/com/ohnosequences/xml/model/BlastOutputParam.java]: ../../ohnosequences/xml/model/BlastOutputParam.java.md
[main/java/com/ohnosequences/xml/model/Overlap.java]: ../../ohnosequences/xml/model/Overlap.java.md
[main/java/com/ohnosequences/xml/model/HspSet.java]: ../../ohnosequences/xml/model/HspSet.java.md
[main/java/com/ohnosequences/xml/model/bio4j/UniprotDataXML.java]: ../../ohnosequences/xml/model/bio4j/UniprotDataXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jPropertyXML.java]: ../../ohnosequences/xml/model/bio4j/Bio4jPropertyXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jRelationshipIndexXML.java]: ../../ohnosequences/xml/model/bio4j/Bio4jRelationshipIndexXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jNodeXML.java]: ../../ohnosequences/xml/model/bio4j/Bio4jNodeXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jNodeIndexXML.java]: ../../ohnosequences/xml/model/bio4j/Bio4jNodeIndexXML.java.md
[main/java/com/ohnosequences/xml/model/bio4j/Bio4jRelationshipXML.java]: ../../ohnosequences/xml/model/bio4j/Bio4jRelationshipXML.java.md
[main/java/com/ohnosequences/xml/model/PredictedGenes.java]: ../../ohnosequences/xml/model/PredictedGenes.java.md
[main/java/com/ohnosequences/xml/model/ncbi/NCBITaxonomyNodeXML.java]: ../../ohnosequences/xml/model/ncbi/NCBITaxonomyNodeXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/GraphmlXML.java]: ../../ohnosequences/xml/model/graphml/GraphmlXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/GraphXML.java]: ../../ohnosequences/xml/model/graphml/GraphXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/KeyXML.java]: ../../ohnosequences/xml/model/graphml/KeyXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/NodeXML.java]: ../../ohnosequences/xml/model/graphml/NodeXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/EdgeXML.java]: ../../ohnosequences/xml/model/graphml/EdgeXML.java.md
[main/java/com/ohnosequences/xml/model/graphml/DataXML.java]: ../../ohnosequences/xml/model/graphml/DataXML.java.md
[main/java/com/ohnosequences/xml/model/Codon.java]: ../../ohnosequences/xml/model/Codon.java.md
[main/java/com/ohnosequences/util/fasta/FastaUtil.java]: ../../ohnosequences/util/fasta/FastaUtil.java.md
[main/java/com/ohnosequences/util/file/GenomeFilesParser.java]: ../../ohnosequences/util/file/GenomeFilesParser.java.md
[main/java/com/ohnosequences/util/file/FnaFileFilter.java]: ../../ohnosequences/util/file/FnaFileFilter.java.md
[main/java/com/ohnosequences/util/file/RntFileFilter.java]: ../../ohnosequences/util/file/RntFileFilter.java.md
[main/java/com/ohnosequences/util/file/PttFileFilter.java]: ../../ohnosequences/util/file/PttFileFilter.java.md
[main/java/com/ohnosequences/util/file/FileUtil.java]: ../../ohnosequences/util/file/FileUtil.java.md
[main/java/com/ohnosequences/util/statistics/StatisticalValues.java]: ../../ohnosequences/util/statistics/StatisticalValues.java.md
[main/java/com/ohnosequences/util/Pair.java]: ../../ohnosequences/util/Pair.java.md
[main/java/com/ohnosequences/util/pal/PalindromicityAnalyzer.java]: ../../ohnosequences/util/pal/PalindromicityAnalyzer.java.md
[main/java/com/ohnosequences/util/Entry.java]: ../../ohnosequences/util/Entry.java.md
[main/java/com/ohnosequences/util/go/GOExporter.java]: ../../ohnosequences/util/go/GOExporter.java.md
[main/java/com/ohnosequences/util/uniprot/UniprotProteinRetreiver.java]: ../../ohnosequences/util/uniprot/UniprotProteinRetreiver.java.md
[main/java/com/ohnosequences/util/oric/OricDataRetriever.java]: ../../ohnosequences/util/oric/OricDataRetriever.java.md
[main/java/com/ohnosequences/util/blast/BlastSubset.java]: ../../ohnosequences/util/blast/BlastSubset.java.md
[main/java/com/ohnosequences/util/blast/BlastExporter.java]: ../../ohnosequences/util/blast/BlastExporter.java.md
[main/java/com/ohnosequences/util/model/PalindromicityResult.java]: ../../ohnosequences/util/model/PalindromicityResult.java.md
[main/java/com/ohnosequences/util/model/Intergenic.java]: ../../ohnosequences/util/model/Intergenic.java.md
[main/java/com/ohnosequences/util/model/Feature.java]: ../../ohnosequences/util/model/Feature.java.md
[main/java/com/ohnosequences/util/genbank/GBCommon.java]: ../../ohnosequences/util/genbank/GBCommon.java.md
[main/java/com/ohnosequences/util/CodonUtil.java]: ../../ohnosequences/util/CodonUtil.java.md
[main/java/com/ohnosequences/util/security/MD5.java]: ../../ohnosequences/util/security/MD5.java.md
[main/java/com/ohnosequences/util/Executable.java]: ../../ohnosequences/util/Executable.java.md
[main/java/com/ohnosequences/util/ExecuteFromFile.java]: ../../ohnosequences/util/ExecuteFromFile.java.md
[main/java/com/ohnosequences/util/seq/SeqUtil.java]: ../../ohnosequences/util/seq/SeqUtil.java.md
[main/java/com/ohnosequences/util/BitOperations.java]: ../../ohnosequences/util/BitOperations.java.md
[main/java/com/ohnosequences/util/ncbi/TaxonomyLoader.java]: ../../ohnosequences/util/ncbi/TaxonomyLoader.java.md
[main/java/com/ohnosequences/util/gephi/GephiExporter.java]: ../../ohnosequences/util/gephi/GephiExporter.java.md
[main/java/com/ohnosequences/util/gephi/GexfToDotExporter.java]: ../../ohnosequences/util/gephi/GexfToDotExporter.java.md
[main/java/com/ohnosequences/aws/util/AvailabilityZones.java]: ../../ohnosequences/aws/util/AvailabilityZones.java.md
[main/java/com/ohnosequences/aws/util/CredentialsRetriever.java]: ../../ohnosequences/aws/util/CredentialsRetriever.java.md
[main/java/com/ohnosequences/aws/util/Endpoints.java]: ../../ohnosequences/aws/util/Endpoints.java.md
[main/java/com/ohnosequences/aws/util/InstanceTypes.java]: ../../ohnosequences/aws/util/InstanceTypes.java.md
[main/java/com/ohnosequences/aws/util/AMITypes.java]: ../../ohnosequences/aws/util/AMITypes.java.md
[main/java/com/ohnosequences/aws/s3/S3FileUploader.java]: ../../ohnosequences/aws/s3/S3FileUploader.java.md
[main/java/com/ohnosequences/aws/s3/S3FileDownloader.java]: ../../ohnosequences/aws/s3/S3FileDownloader.java.md
[main/java/com/ohnosequences/aws/ec2/SpotUtil.java]: ../../ohnosequences/aws/ec2/SpotUtil.java.md
[main/java/com/ohnosequences/aws/ec2/InstanceUtil.java]: ../../ohnosequences/aws/ec2/InstanceUtil.java.md