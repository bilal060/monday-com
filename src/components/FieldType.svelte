<script>
    import { Col, Row } from "sveltestrap";
    import "./scss/FieldType.scss";
    let currentColor = "#6c757d";
    import IconButton, { Icon } from '@smui/icon-button';
    import { Svg } from '@smui/common/elements';
    import { mdiCalendarBlank, mdiFormDropdown, mdiAccountBox, mdiFormatText, mdiNumeric, mdiRestore, mdiSitemap, mdiSigma, mdiInformationOutline } from '@mdi/js';
</script>

<div class="field-type-popup">
    <div class="field-type-content">
        <ul class="row field-list">
           <li class="col-6">
               <div class="field-item">
                    <i class="field-icon status-icon" style={"background-image: url('/images/status-bar.png')"}></i>
                    <span class="field-text">Status</span>
               </div>
           </li> 

           <li class="col-6">
                <div class="field-item">
                    <i class="field-icon">
                        <Icon width={20} height={20} component={Svg} viewBox="0 0 24 24">
                            <path fill="{currentColor}" d={mdiCalendarBlank} />
                        </Icon>
                    </i>
                    <span class="field-text">Date</span>
                </div>
            </li> 

            <li class="col-6">
                <div class="field-item">
                    <Icon width={20} height={20} component={Svg} viewBox="0 0 24 24">
                        <path fill="{currentColor}" d={ mdiFormDropdown } />
                    </Icon>
                    <span class="field-text">Dropdown</span>
                </div> 
            </li> 

            <li class="col-6">
                <div class="field-item">
                    <Icon width={20} height={20} component={Svg} viewBox="0 0 24 24">
                        <path fill="{currentColor}" d={mdiAccountBox} />
                    </Icon>
                    <span class="field-text">People</span>
                </div>
            </li> 

            <li class="col-6">
                <div class="field-item">
                    <Icon width={20} height={20} component={Svg} viewBox="0 0 24 24">
                        <path fill="{currentColor}" d={mdiFormatText} />
                    </Icon>
                    <span class="field-text">Text</span>
                </div>
            </li> 

            <li class="col-6">
                <div class="field-item">
                    <Icon width={20} height={20} component={Svg} viewBox="0 0 24 24">
                        <path fill="{currentColor}" d={ mdiNumeric } />
                    </Icon>
                    <span class="field-text">Numbers</span>
                </div>
            </li> 

            <li class="col-6">
                <div class="field-item">
                    <Icon width={20} height={20} component={Svg} viewBox="0 0 24 24">
                        <path fill="{currentColor}" d={ mdiRestore } />
                    </Icon>
                    <span class="field-text">Last Updated</span>
                </div>
            </li> 

            <li class="col-6">
                <div class="field-item">
                    <Icon width={20} height={20} component={Svg} viewBox="0 0 24 24">
                        <path fill="{currentColor}" d={ mdiSitemap } />
                    </Icon>
                    <span class="field-text">Work Flow</span>
                </div>
            </li> 

            <li class="col-6">
                <div class="field-item">
                    <Icon width={20} height={20} component={Svg} viewBox="0 0 24 24">
                        <path fill="{currentColor}" d={ mdiSigma } />
                    </Icon>
                    <span class="field-text">Formula</span>
                </div>
            </li> 

            <li class="col-6">
                <div class="field-item">
                    <Icon width={20} height={20} component={Svg} viewBox="0 0 24 24">
                        <path fill="{currentColor}" d={ mdiInformationOutline } />
                    </Icon>
                    <span class="field-text">Creation Log</span>
                </div>
            </li> 
        </ul>
    </div>
</div>



